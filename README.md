# PRIMITIVE-10

### A REAL CALCULATOR. BUILT CIRCUIT BY CIRCUIT.

**72 CUSTOM CIRCUITS · 10-DIGIT DECIMAL ARITHMETIC · FULLY WORKING**

![PRIMITIVE-10 — Electric Calculator](assets/images/cover.png)

**PRIMITIVE-10 is a fully functional electronic calculator built inside Geareo using custom circuit logic.**

This is not a calculator-shaped decoration. It is an actual computational system: it accepts input, processes arithmetic operations, manages memory, stores results, handles errors, and drives a physical 10-position display.

No precomputed answer tables. No external calculator engine. The arithmetic and control logic are implemented inside the game.

**72 circuits. 43 functions. 29 modules. Approximately one month of development.**

---

## THE NUMBERS BEHIND THE MACHINE

| Specification | PRIMITIVE-10 v1.0 |
|---|---|
| Custom circuits | **72** |
| Functions | **43** |
| Modules | **29** |
| Internal arithmetic precision | **10 significant decimal digits** |
| Internal exponent range | **−999999 to +999999** |
| Arithmetic operations | **+, −, ×, ÷** |
| Display | **10 digit positions + separate M indicator** |
| Controls | **23 active buttons** |
| Memory | **M+, M−, MR, MC** |
| Display formats | **Automatic FIXED / SCIENTIFIC** |

The internal decimal range extends from magnitudes as small as **1 × 10^-999999** up to **9.999999999 × 10^999999**, with positive and negative values.

These are internal arithmetic limits. The physical display has only 10 positions, so some numbers require rounding or cannot be displayed.

---

## WHAT CAN IT ACTUALLY DO?

### 1. Full Decimal Arithmetic

PRIMITIVE-10 supports all four standard arithmetic operations:

- **Addition (+)** and **Subtraction (−)**
- **Multiplication (×)**
- **Division (÷)**
- Negative and fractional operands
- Automatic decimal normalization and rounding

Division is implemented using custom multi-precision long-division logic, not a built-in calculator operation.

### 2. Chained Calculations

Continue working with the current result without clearing the calculator.

Example:

`12 + 3 − 2 =` → **13**

The calculator maintains its accumulated result and executes pending operations as new operations are entered.

### 3. Repeated Equals

The calculator remembers the last operation and its second operand.

Example:

`6 + 2 =` → **8**

`=` → **10**

`=` → **12**

This also works with division:

`100 ÷ 4 =` → **25**

`=` → **6.25**

`=` → **1.5625**

### 4. Implicit Second Operand

You do not always need to enter the second number.

Example:

`6 + =` → **12**

`=` → **18**

`=` → **24**

When the second operand has not been explicitly entered, the calculator can reuse the first operand.

### 5. Four-Function Memory

A separate memory register is available through:

| Button | Function |
|---|---|
| **M+** | Add the current number to memory |
| **M−** | Subtract the current number from memory |
| **MR** | Recall the stored number |
| **MC** | Clear memory |

A dedicated **M indicator** lights when memory contains a nonzero number.

Memory Recall can also supply an operand to a pending arithmetic operation.

**Important:** Pressing C clears the calculation and input state but preserves memory. Only MC clears the memory register.

### 6. Decimal Entry and Editing

The calculator supports:

- Decimal point entry
- Sign toggle (+/−)
- Backspace (BSP)
- Clear (C)
- Up to 10 physical display positions

While entering a number, the display preserves what was typed, including decimal placement and trailing zeros. The number is normalized for arithmetic when needed.

### 7. Automatic Scientific Notation

There is no manual display-mode switch.

PRIMITIVE-10 automatically chooses between ordinary decimal display (**FIXED**) and exponent notation (**SCIENTIFIC**) based on the number and available display space.

Examples:

`1000000000 ÷ 0.1 =` → **1E10**

`1 ÷ 1000000000 =` → **0.000000001**

Press `=` again → **1E-18**

The internal result remains separate from the rounded value shown on the display.

### 8. Error Handling

The calculator detects conditions such as:

- Division by zero
- Arithmetic exponent overflow
- Results that cannot fit within the supported display format

When an error occurs, the display shows **ErrOr**, and the calculator enters a dedicated error state.

Press **C** to clear the error and start a new calculation. Stored memory is preserved.

---

## WHAT'S UNDER THE HOOD?

**This is where PRIMITIVE-10 becomes more than a calculator.**

Its arithmetic does not rely on a single native floating-point value to store a 10-digit mantissa.

Instead, the system uses a custom decimal number representation:

`Number = [Hi, Lo, Exp, Neg]`

- **Hi + Lo:** Two separate five-digit chunks forming a normalized 10-digit mantissa.
- **Exp:** Decimal exponent.
- **Neg:** Sign flag.

This approach allows PRIMITIVE-10 to perform higher-precision decimal calculations while keeping individual arithmetic operations within the numerical precision limits of Geareo.

### Custom Arithmetic Unit

The four arithmetic operations have their own implementations:

- **Addition / subtraction:** Magnitude ordering, decimal alignment, wide arithmetic, and normalization.
- **Multiplication:** Partial products and carry propagation across decimal chunks.
- **Division:** Base-100 long division, quotient estimation, correction, and rounding.

### Complete Control Architecture

Behind the buttons and display is a stateful control system.

It includes:

- Input capture and command decoding
- ENTRY, RESULT, and ERROR modes
- Dedicated entry, calculation, and memory controllers
- Candidate/Current state storage
- Transaction synchronization and commit phases
- Display formatting and rendering
- Safe error handling

Each command is processed as a controlled transaction before the next command can execute.

**The calculator is not one giant formula. It is a complete interconnected circuit system.**

---

## TECHNICAL DOCUMENTATION

**This repository exists primarily to preserve the complete technical documentation and the original Geareo project backup.**

The documentation is available in **English and Ukrainian**.

| Document | English | Українська |
|---|---|---|
| **System Architecture** — Overall design, data flow, state management, synchronization, display, and reconstruction | [docs.txt](docs/EN/docs.txt) | [docs_ua.txt](docs/UA/docs_ua.txt) |
| **Contracts** — Number formats, interfaces, invariants, timing, and behavioral rules | [contracts.txt](docs/EN/contracts.txt) | [contracts_ua.txt](docs/UA/contracts_ua.txt) |
| **Functions** — All 43 circuit functions, formulas, ports, and implementation details | [functions.txt](docs/EN/functions.txt) | [functions_ua.txt](docs/UA/functions_ua.txt) |
| **Modules** — All 29 circuit modules, internal wiring, and controller architecture | [modules.txt](docs/EN/modules.txt) | [modules_ua.txt](docs/UA/modules_ua.txt) |

Together, these documents describe all **72 custom circuits**, their interfaces, the arithmetic algorithms, and how the complete calculator operates.

---

## DOWNLOAD AND PROJECT BACKUP

**[Download PRIMITIVE-10 v1.0 — GitHub Release](https://github.com/TheOnefor/PRIMITIVE-10/releases/tag/v1.0)**

The release contains the original Geareo project backup:

`PRIMITIVE-10_v1.0.zip`

This archive is intended for project preservation and backup, not as a standalone executable calculator.

The repository and its documentation provide an archival record of the system's architecture and implementation.

---

## STEAM WORKSHOP

### [▶ PLAY PRIMITIVE-10 IN GEAREO — STEAM WORKSHOP](https://steamcommunity.com/sharedfiles/filedetails/?id=3816680387)

**Want to try the calculator yourself?**

Subscribe to the Workshop item and open it in Geareo to interact with the fully working PRIMITIVE-10.

---

## CREDITS

**PRIMITIVE-10 v1.0**

Created by **TheOneFor**

Built in **Geareo**.

**ONE MONTH OF DEVELOPMENT. 72 CIRCUITS. ONE FULLY WORKING MACHINE.**
