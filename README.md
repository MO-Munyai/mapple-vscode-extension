# Mapple VS Code Extension

VS Code language support for the Mapple Programming Language (MPPL).

## Purpose

This repository contains the Visual Studio Code extension for Mapple.

The goal is to provide a first-class development experience for `.mp` files, including:

* Syntax highlighting
* Language configuration
* Bracket matching
* Auto-closing pairs
* Comment support
* Snippets
* Diagnostics (future)
* IntelliSense (future)
* LSP integration (future)

This project is separate from the Mapple compiler so editor tooling can evolve independently.

---

# Why This Exists

Mapple is becoming large enough that development productivity matters.

Currently, `.mp` files are treated as plain text.

This extension will allow:

```mapple
let int age = 20;

age = age + 1;

print(age.str);
```

to be displayed with proper syntax highlighting and editor support.

Long term, the goal is for Mapple development to feel similar to writing Python, Java, or TypeScript inside VS Code.

---

# Relationship To Mapple

Current Mapple compiler:

```text
Mapple Source (.mp)
        ↓
Lexer
        ↓
Parser
        ↓
AST
        ↓
Semantic Analysis
        ↓
Python Code Generation
        ↓
Execution
```

This extension does not compile code.

Its responsibility is editor tooling only.

---

# Development Roadmap

## Phase 1 - Basic Language Recognition

Goal:

VS Code recognizes `.mp` files as Mapple.

Tasks:

* Register `.mp` extension
* Define language identifier
* Add basic language configuration

Success:

Opening a `.mp` file automatically activates the extension.

---

## Phase 2 - Syntax Highlighting

Goal:

Mapple code is colorized.

Highlight:

Keywords:

```text
let
func
class
print
input
```

Types:

```text
int
num
str
char
bool
```

Literals:

```text
123
3.14
"hello"
'A'
true
false
```

Comments:

```text
//
/* */
```

Success:

Mapple code is visually distinguishable and readable.

---

## Phase 3 - Editor Experience

Goal:

Make writing Mapple pleasant.

Features:

* Auto-close parentheses
* Auto-close quotes
* Auto-indent
* Comment toggling
* Bracket matching

Success:

Mapple behaves similarly to other supported languages.

---

## Phase 4 - Snippets

Goal:

Reduce typing.

Examples:

Typing:

```text
let
```

expands to:

```mapple
let <type> <name> = ;
```

Typing:

```text
func
```

expands to:

```mapple
func FunctionName():
    
;
```

Success:

Common Mapple structures can be generated quickly.

---

## Phase 5 - Diagnostics

Goal:

Surface compiler errors inside VS Code.

Examples:

* Undeclared variables
* Type mismatches
* Invalid assignments

Potential implementation:

Run the Mapple compiler in the background and display diagnostics through VS Code APIs.

---

## Phase 6 - Language Server (LSP)

Goal:

Provide advanced IDE features.

Features:

* Go to Definition
* Find References
* Rename Symbol
* Hover Information
* Auto-completion

Success:

Mapple development feels comparable to mainstream languages.

---

# Suggested Technology Stack

## Version 1

TextMate Grammar

Used for:

* Syntax highlighting

Files:

```text
syntaxes/mapple.tmLanguage.json
```

---

## Version 2

VS Code Extension API

Used for:

* Language registration
* Snippets
* Diagnostics

Files:

```text
package.json
language-configuration.json
```

---

## Version 3

Language Server Protocol (LSP)

Used for:

* IntelliSense
* Symbol navigation
* Refactoring

---

# Repository Structure

```text
mapple-vscode-extension/

├── README.md
├── package.json
├── language-configuration.json

├── syntaxes/
│   └── mapple.tmLanguage.json

├── snippets/
│   └── mapple.json

└── examples/
    └── sample.mp
```

---

# Prerequisites

Required:

* Node.js
* npm
* Visual Studio Code

Recommended:

* TypeScript
* VS Code Extension Generator

Install:

```bash
npm install -g yo generator-code
```

Generate extension:

```bash
yo code
```

Choose:

```text
New Language Support Extension
```

Language Name:

```text
Mapple
```

Language ID:

```text
mapple
```

File Extension:

```text
.mp
```

---

# Definition Of Done (v1)

A user installs the extension.

Opening:

```mapple
let int age = 20;

print(age.str);
```

automatically:

* Recognizes the file as Mapple
* Applies syntax highlighting
* Supports comments
* Supports indentation
* Supports bracket matching

At that point, Mapple has its first editor integration.
