# Release notes

- **0.7.0 WIP**
  - (!) refactor: `ScalableNumber` renamed to `QuantityValue`
  - refactor: basic concepts, `quantity` and `quantity_cast` refactored
  - feat: interoperability with `std::chrono::duration` and other units libraries
  - feat: CTAD for dimensionless quantity added
  - feat: value initialization for quantity value removed (left with a default initialization)
  - perf: preconditions check do not influence the runtime performance of a Release build
  - perf: `quantity_cast()` generates less assembly instructions
  - perf: temporary string creation removed from `quantity::op<<()`
  - fix: `quantity_cast()` fixed to work correctly with representation types not convertible from `std::intmax_t`
  - fix: ambiguous case for empty type list resolved
  - build: doxygen updated to 1.8.20
  - ci: CI switched from Travis CI to GitHub Actions

- **0.6.0 September 13, 2020**
  - feat: `quantity_point` support added (thanks [@johelegp](https://github.com/johelegp))
  - feat: Added angle as SI base dimension (thanks [@kwikius](https://github.com/kwikius))
  - feat: `si::angular_velocity` support added (thanks [@mikeford3](https://github.com/mikeford3))
  - feat: FPS system added (thanks [@mikeford3](https://github.com/mikeford3))
  - feat: Added support for mathematical function `exp(quantity)`
  - feat: Localization support for text output added (thanks [@rbrugo](https://github.com/rbrugo))
  - feat: Added STL random number distribution wrappers (thanks [@yasamoka](https://github.com/yasamoka))
  - (!) refactor: Refactored and cleaned up the library file tree
  - (!) refactor: `q_*` UDL renamed to `_q_*`
  - (!) refactor: UDLs with "per" in name renamed from `*p*` to `*_per_*`
  - (!) refactor: `ratio` changed to the NTTP kind
  - (!) refactor: `exp` and `Exp` renamed to `exponent` and `Exponent`
  - (!) refactor: `Scalar` concept renamed to `ScalableNumber`
  - (!) refactor: Dimensionless quantities redesigned to be of a `quantity` type
  - refactor: `math.h` function signatures refactored to use a `Quantity` concept (thanks [@kwikius](https://github.com/kwikius))
  - refactor: `[[nodiscard]]` added to many functions
  - fix: `si::day` unit symbol fixed to `d` (thanks [@komputerwiz](https://github.com/komputerwiz))
  - fix: `si::mole` unit symbol fixed to `mol` (thanks [@mikeford3](https://github.com/mikeford3))
  - (!) build: gcc-9 is no longer supported (at least gcc-10 is required)
  - build: Visual Studio 16.7 support added
  - build: linear_algebra updated to 0.7.0/stable
  - build: fmt updated to 7.0.3
  - build: range-v3 updated to 0.11.0
  - build: catch2 updated to 2.13.0
  - build: doxygen updated to 1.8.18
  - build: ms-gsl 3.1.0 dependency added
  - build: Removed the dependency on a git submodule with common CMake scripts

- **0.5.0 May 17, 2020**
  - Major refactoring and rewrite of the library
  - Units are now independent from dimensions
  - Dimensions now depend on units (base or coherent units are provided in a class template)
  - Quantity gets a Dimension template parameter again (as unit does not provide information about
    its dimension anymore)
  - Spaceship operator support added
  - Added official CGS system support
  - Added official data information system support
  - Repository file tree cleanup
  - `ratio` refactored to contain `Exp` template parameter (thanks a lot [@oschonrock](https://github.com/oschonrock)!)
  - SI fundamental constants added
  - `q_` prefix applied to all the UDLs (thanks [@kwikius](https://github.com/kwikius))
  - `unknown_unit` renamed to `unknown_coherent_unit`
  - Project documentation greatly extended and switched to Sphinx
  - A few more usage examples added
  - ASCII-only output support added (thanks [@yasamoka](https://github.com/yasamoka))
  - Representation values formatting extended (thanks [@rbrugo](https://github.com/rbrugo))
  - Output streams formatting support added
  - Linear algebra from `std::experimental::math` support added
  - Named SI units and their dimensions added (thanks [@rbrugo](https://github.com/rbrugo)
  - libfmt updated to 6.2.0
  - Added absolute functions and epsilon to math.h (thanks [@mikeford3](https://github.com/mikeford3))
  - Added a lot of prefixes to named units and introduced `alias_unit` (thanks [@yasamoka](https://github.com/yasamoka))
  - Linking with Conan targets only when they exists ([#98](https://github.com/mpusz/units/issues/98))
  - All physical dimensions and units put into `physical` namespace
  - CMake improvements
  - Velocity renamed to speed

  Many thanks to GitHub users [@oschonrock](https://github.com/oschonrock),
  [@kwikius](https://github.com/kwikius), and [@i-ky](https://github.com/i-ky) for their support
  in drafting a new library design.

- **0.4.0 Nov 17, 2019**
  - Support for derived dimensions in `exp` added
  - Added `pow()` and `sqrt()` operations on quantities
  - `units` removed from a `std::experimental` namespace
  - Downcasting facility refactored so the user does not have to write the boilerplate code anymore
  - From now on base dimensions should inherit from `base_dimension` class template
  - Added unit symbols definitions to `base_dimension` and derived units
  - Added support for `operator<<` on `quantity`
  - `fmt` support added
  - Derived unit factory helpers refactored
  - Refactored the way prefixed units are defined

- **0.3.1 Sep 18, 2019**
  - cmcstl2 dependency changed to range-v3 0.9.1

- **0.3.0 Sep 16, 2019 (CppCon 2019 design)**
  - The design as described on CppCon 2019 talk (<https://youtu.be/0YW6yxkdhlU>)
  - Applied the feedback from the Cologne evening session
    - `upcasting_traits` renamed to `downcasting_traits`
    - `Dimension` template parameter removed from quantity
  - `units` moved to a `std::experimental` namespace
  - Leading underscore prefix removed from UDLs
  - Added a few more derived dimensions
  - `meter` renamed to `metre`
  - Missing `operator*` added
  - Predefined dimensions moved to a dedicated directory
  - `dimension_` prefix removed from names of derived dimensions
  - cmcstl2 library updated to 2019.09.19
  - `base_dimension` is a value provided as `const&` to the `exp` type
  - integrated with Compiler Explorer
  - gsl-lite dependency removed
  - Fractional dimension exponents support added
  - `QuantityOf` concept introduced
  - `quantity_cast<U, Rep>()` support added

- **0.2.0 July 18, 2019 (C++Now 2019 design)**
  - The design as described on C++Now 2019 talk (<https://youtu.be/wKchCktZPHU>)
  - Added C++20 features supported by gcc-9.1 (`std::remove_cvref_t`, down with typename, `std::type_identity`)
  - Compile-time performance optimizations (`type_list`, `common_ratio`, `ratio`, `conditional_t`)

- **0.1.0 May 18, 2019**
  - Initial library release
  - Begin semantic versioning
  - The last version to work with gcc-8
