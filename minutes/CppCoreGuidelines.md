## P: Philosophy

Should be read by everyone.

| Code   | Name                                                                   | Vote | Comment                                                                         |
|--------|------------------------------------------------------------------------|------|---------------------------------------------------------------------------------|
| [P.1]  | Express ideas directly in code                                         | 3    |                                                                                 |
| [P.2]  | Write in ISO Standard C++                                              | 3    |                                                                                 |
| [P.3]  | Express intent                                                         | 3/4  | Ranged for loops (lang-tidy)                                                    |
| [P.4]  | Ideally, a program should be statically type safe                      | 3    | void*, Bottle, Properties, loosely typed types should not be passed around      |
| [P.5]  | Prefer compile-time checking to run-time checking                      | 3    |                                                                                 |
| [P.6]  | What cannot be checked at compile time should be checkable at run time | 3    |                                                                                 |
| [P.7]  | Catch run-time errors early                                            | 3    |                                                                                 |
| [P.8]  | Don’t leak any resources                                               | 3/4  | We should start changing owned raw pointers with smart ptrs                     |
| [P.9]  | Don’t waste time or space                                              | 3    |                                                                                 |
| [P.10] | Prefer immutable data to mutable data                                  | 3    |                                                                                 |
| [P.11] | Encapsulate messy constructs, rather than spreading through the code   | 3    |                                                                                 |
| [P.12] | Use supporting tools as appropriate                                    | 4    |                                                                                 |
| [P.13] | Use support libraries as appropriate                                   | 2/4  | STL ok, other later maybe, maybe import functionalities                         |

[P.1]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p1-express-ideas-directly-in-code "P.1: Express ideas directly in code"
[P.2]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p2-write-in-iso-standard-c "P.2: Write in ISO Standard C++"
[P.3]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p3-express-intent "P.3: Express intent"
[P.4]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p4-ideally-a-program-should-be-statically-type-safe "P.4: Ideally, a program should be statically type safe"
[P.5]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p5-prefer-compile-time-checking-to-run-time-checking "P.5: Prefer compile-time checking to run-time checking"
[P.6]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p6-what-cannot-be-checked-at-compile-time-should-be-checkable-at-run-time "P.6: What cannot be checked at compile time should be checkable at run time"
[P.7]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p7-catch-run-time-errors-early "P.7: Catch run-time errors early"
[P.8]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p8-dont-leak-any-resources "P.8: Don’t leak any resources"
[P.9]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p9-dont-waste-time-or-space "P.9: Don’t waste time or space"
[P.10]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p10-prefer-immutable-data-to-mutable-data "P.10: Prefer immutable data to mutable data"
[P.11]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p11-encapsulate-messy-constructs-rather-than-spreading-through-the-code "P.11: Encapsulate messy constructs, rather than spreading through the code"
[P.12]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p12-use-supporting-tools-as-appropriate "P.12: Use supporting tools as appropriate"
[P.13]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#p13-use-support-libraries-as-appropriate "P.13: Use support libraries as appropriate"

---

## I: Interfaces

API.


| Code   | Name                                                                   | Vote | Comment                                                                         |
|--------|------------------------------------------------------------------------|------|---------------------------------------------------------------------------------|
| [I.1]  | Make interfaces explicit                                               | 2    | Check again later (probably already in use)                                     |
| [I.2]  | Avoid non-`const` global variables                                     | 2    | Check again later (probably already in use)                                     |
| [I.3]  | Avoid singletons                                                       | 1/2  | Non now, investigate alternatives later                                         |
| [I.4]  | Make interfaces precisely and strongly typed                           | 3    | Start looking at void*                                                          |
| [I.5]  | State preconditions (if any)                                           | 2    | `YARP_EXPECTS` macro?                                                           |
| [I.6]  | Prefer `Expects()` for expressing preconditions                        | 2    | `yExpects()` + unlikely                                                         |
| [I.7]  | State postconditions                                                   | 2    | `YARP_ENSURES` macro?                                                           |
| [I.8]  | Prefer `Ensures()` for expressing postconditions                       | 2    | `yEnsures()` + unlikely                                                         |
| [I.9]  | If an interface is a template, document its parameters using concepts  | 1/2  |                                                                                 |
| [I.10] | Use exceptions to signal a failure to perform a required task          | 0    |                                                                                 |
| [I.11] | Never transfer ownership by a raw pointer (`T*`) or reference (`T&`)   | 3    | `gsl::owner`?                                                                   |
| [I.12] | Declare a pointer that must not be null as `not_null`                  | 1    |                                                                                 |
| [I.13] | Do not pass an array as a single pointer                               | 2    | `span`                                                                          |
| [I.22] | Avoid complex initialization of global objects                         | 3    |                                                                                 |
| [I.23] | Keep the number of function arguments low                              | 3    |                                                                                 |
| [I.24] | Avoid adjacent unrelated parameters of the same type                   | 3    |                                                                                 |
| [I.25] | Prefer abstract classes as interfaces to class hierarchies             | 3    |                                                                                 |
| [I.26] | If you want a cross-compiler ABI, use a C-style subset                 | ?    |                                                                                 |
| [I.27] | For stable library ABI, consider the Pimpl idiom                       | 3/4  | [Smart Pimpl] + const + struct                                                  |
| [I.30] | Encapsulate rule violations                                            | 3    | .                                                                               |

[I.1]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i1-make-interfaces-explicit "I.1: Make interfaces explicit"
[I.2]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i2-avoid-non-const-global-variables "I.2: Avoid non-const global variables"
[I.3]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i3-avoid-singletons "I.3: Avoid singletons"
[I.4]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i4-make-interfaces-precisely-and-strongly-typed "I.4: Make interfaces precisely and strongly typed"
[I.5]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i5-state-preconditions-if-any "I.5: State preconditions (if any)"
[I.6]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i6-prefer-expects-for-expressing-preconditions "I.6: Prefer Expects() for expressing preconditions"
[I.7]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i7-state-postconditions "I.7: State postconditions"
[I.8]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i8-prefer-ensures-for-expressing-postconditions "I.8: Prefer Ensures() for expressing postconditions"
[I.9]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i9-if-an-interface-is-a-template-document-its-parameters-using-concepts "I.9: If an interface is a template, document its parameters using concepts"
[I.10]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i10-use-exceptions-to-signal-a-failure-to-perform-a-required-task "I.10: Use exceptions to signal a failure to perform a required task"
[I.11]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i11-never-transfer-ownership-by-a-raw-pointer-t-or-reference-t "I.11: Never transfer ownership by a raw pointer (T*) or reference (T&)"
[I.12]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i12-declare-a-pointer-that-must-not-be-null-as-not_null "I.12: Declare a pointer that must not be null as not_null"
[I.13]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i13-do-not-pass-an-array-as-a-single-pointer "I.13: Do not pass an array as a single pointer"
[I.22]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i22-avoid-complex-initialization-of-global-objects "I.22: Avoid complex initialization of global objects"
[I.23]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i23-keep-the-number-of-function-arguments-low "I.23: Keep the number of function arguments low"
[I.24]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i24-avoid-adjacent-unrelated-parameters-of-the-same-type "I.24: Avoid adjacent unrelated parameters of the same type"
[I.25]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i25-prefer-abstract-classes-as-interfaces-to-class-hierarchies "I.25: Prefer abstract classes as interfaces to class hierarchies"
[I.26]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i26-if-you-want-a-cross-compiler-abi-use-a-c-style-subset "I.26: If you want a cross-compiler ABI, use a C-style subset"
[I.27]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i27-for-stable-library-abi-consider-the-pimpl-idiom "I.27: For stable library ABI, consider the Pimpl idiom"
[I.30]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#i30-encapsulate-rule-violations "I.30: Encapsulate rule violations"
[Smart Pimpl]: http://oliora.github.io/2015/12/29/pimpl-and-rule-of-zero.html

---


## F: Functions

*TODO*

---

## C: Classes and class hierarchies

| Code   | Name                                                                   | Vote | Comment                                                                         |
|--------|------------------------------------------------------------------------|------|---------------------------------------------------------------------------------|
| [C.1]  | Organize related data into structures (`structs` or `classes`)         | 3    |                                                                                 |
| [C.2]  | Use `class` if the class has an invariant; use `struct` if the data... | 0    |                                                                                 |
| [C.3]  | Represent the distinction between an interface and an implementatio... | 3    | Ok, but use pimpl for libraries                                                 |
| [C.4]  | Make a function a member only if it needs direct access to the repr... | 3    |                                                                                 |
| [C.5]  | Place helper functions in the same namespace as the class they support | 3    |                                                                                 |
| [C.7]  | Don’t define a class or enum and declare a variable of its type in ... | 3    | Already in use                                                                  |
| [C.8]  | Use `class` rather than `struct` if any member is non-public           | 3    |                                                                                 |
| [C.9]  | Minimize exposure of members                                           | 3    | Already in use                                                                  |
| [C.10] | Prefer concrete types over class hierarchies                           | 0/1  |                                                                                 |
| [C.11] | Make concrete types regular                                            | 2    |                                                                                 |

[C.1]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c1-organize-related-data-into-structures-structs-or-classes "C.1: Organize related data into structures (structs or classes)"
[C.2]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c2-use-class-if-the-class-has-an-invariant-use-struct-if-the-data-members-can-vary-independently "C.2: Use class if the class has an invariant; use struct if the data members can vary independently"
[C.3]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c3-represent-the-distinction-between-an-interface-and-an-implementation-using-a-class "C.3: Represent the distinction between an interface and an implementation using a class"
[C.4]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c4-make-a-function-a-member-only-if-it-needs-direct-access-to-the-representation-of-a-class "C.4: Make a function a member only if it needs direct access to the representation of a class"
[C.5]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c5-place-helper-functions-in-the-same-namespace-as-the-class-they-support "C.5: Place helper functions in the same namespace as the class they support"
[C.7]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c7-dont-define-a-class-or-enum-and-declare-a-variable-of-its-type-in-the-same-statement "C.7: Don’t define a class or enum and declare a variable of its type in the same statement"
[C.8]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c8-use-class-rather-than-struct-if-any-member-is-non-public "C.8: Use class rather than struct if any member is non-public"
[C.9]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c9-minimize-exposure-of-members "C.9: Minimize exposure of members"
[C.10]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c10-prefer-concrete-types-over-class-hierarchies "C.10: Prefer concrete types over class hierarchies"
[C.11]: https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#c11-make-concrete-types-regular "C.11: Make concrete types regular"
