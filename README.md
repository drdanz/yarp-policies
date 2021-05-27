## All

### Do not use using directives

The use of `using namespace foo` statements is not allowed.

These are not to be confused with using-declarations (using `foo::SomeName`),
which are permitted in `.cpp` files.

*Rationale*: Using-directives are time-bombs: code that compiles today could
easily stop compiling with the next language version or symbol addition. They
are dangerous enough to be banned by the Google style guide.

*See also*:

* https://abseil.io/tips/153


### Assert should not contain logic

Do not insert code that should always be executed.

For example this is ok:

```
yarp::os::Port p;
[[maybe_unused]] bool ret = p.open("...");
yAssert(ret);
```

but this is not ok, since the port will not be open in release mode:

```
yarp::os::Port p;
yAssert(p.open("..."));
```

*Rationale*: Asserts are disabled in release mode and the code will not be
executed.


## **YL** Libraries

### YL1: All headers containing public classes must be included at least once

All headers containing public virtual classes must be included at least once in
one `.cpp` file that belongs to the library, even if everything is inline.

This does not apply to template classes.

*Rationale*: When the class is imported, the linker looks for the vtable in the
library, but if the file is not included when creating the library, the vtable
is never created.


## **EH** Error Handling

### EH1: Asserts should not be used for error handling

Do not use `assert()`, `yAssert()`, etc. for error handling.

*Rationale*: Asserts are disabled in release mode and will give no feedback at
all when something goes wrong.


### EH2: Termination of the execution should not be used for error handling

Do not use `exit()`, `abort()`, `terminate`, `yFatal()`, etc. for error
handling.

*Rationale*: The user should be allowed, after an error, to close the software
and the hardware cleanly, forcing the program termination will just make it
impossible


## **IF**: YARP interfaces

### IF1: Methods in the interfaces should not return objects that require a destructor

Methods in the interfaces should use only basic types.

*Rationale*: Devices are mostly implemented as plugins, therefore memory
allocated inside the plugin should be deleted inside the plugin itself.
On windows there is a risk that the memory allocated inside the plugin is
deleted after the dll has already been unloaded, therefore it might cause
crashes.


## **YC**: YARP carriers

### YC3: Classes in the carriers plugins should not be in the `yarp::os` namespace

*See YDD3*

## **YDD**: Device drivers

### YDD1: Devices should have only default constructor and destructor

Devices should have only the default constructor and the destructor.
Other constructor and the copy operators should be deleted.

```c++
    NewDevice();
    NewDevice(const NewDevice&) = delete;
    NewDevice(NewDevice&&) = delete;
    NewDevice& operator=(const NewDevice&) = delete;
    NewDevice& operator=(NewDevice&&) = delete;

    ~NewDevice() override;
```

The static `create<DeviceName>` method is not useful unless the device is in
`YARP_dev`, therefore it should not exist.

*Rationale*: Devices should be created using the PolyDriver, that uses the default
constructor


### YDD2: Devices constructor should not allocate memory

The memory allocation should happen only in the `open()` method.

*Rationale*: The plugin system creates and destroys the device twice. This avoids
allocating useless memory that is not used.


### YDD3: Classes in the devices plugins should not be in the `yarp::dev` namespace

*Rationale*: The `yarp::dev` namespace is reserved for classes in the `YARP_dev`
library.

### YDD4: Devices methods should not be `virtual`, but only `override`, unless there is a good reason

*Rationale*: Devices classes derive from interfaces, but they are never derived.

There are a few exception for 2 device sharing the same implementation or some
base class. In this case `virtual` methods are allowed.


## **YNW**: Network Wrapper Client/Server

### YNW1: NWC and NWS should not contain any logic.

*Rationale*: Logic inside NWS/NWC implies that:
  * there is a difference in using the device locally or using an NWC connected
    to an NWS;
  * if there are NWS for different middleware, each of them should implement the
    same logic.


### YNW2: NWC and NWS naming convention.

The name of the device consists of 3 parts, separated by a `_` character:

* A "significative" common part shared by both devices (camelCase, with the
  first word lowercase)
* `nwc` or `nws`.
* The name of the middleware (lowercase) (`yarp`, `ros`, etc.)

For example:

| NWS                             | NWC                             |
|---------------------------------|---------------------------------|
| `controlBoard_nws_yarp`         | `controlBoard_nwc_yarp`         |
| `multipleAnalogSensor_nws_yarp` | `multipleAnalogSensor_nwc_yarp` |


### YNW3: NWC and NWS protocol should be defined using thrift.

*Rationale*:  Historically, the protocol used in YARP NWC and NWS was defined
inside the code.
This requires that the server and client are kept in sync manually, using
parsing of positional arguments inside bottles, makes the code hard to read, and
less maintainable.


## **YBP**: YARP `BufferedPort`

### YBP1: `onRead()` should use `std::swap` to save the `Portable`

When the `onRead()` callback method in a `BufferedPort` should save the data,
if this data is not used anywhere else, it should be saved using `std::swap`

*Rationale*: The `BufferedPort` reuses the data. Moving the data means that
the moved object should not be used again, and in some case the move operator
will leave the `Portable` in an invalid state, which might cause crashes when
used again. Copying the data is usually expansive. Swapping the data with the
previous will ensure that the data owned by the `BufferedPort` will stay in
a consistent (and safe) state, will avoid re-allocating memory, and will avoid
useless copies.
