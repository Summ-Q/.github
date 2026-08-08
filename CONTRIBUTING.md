# Contributing Guidelines

Thank you for contributing! To keep the repository clean and organized, we follow a strict branch naming convention. Please read through these rules before pushing any new branches.

---

## Branch Naming Convention

All branches must follow this exact structure:
`type/description`

### 1. Allowed Types
Every new branch must be prefixed with one of the following types, depending on the nature of your work:

* **`feature`** or **`feat`**: For new features or structural additions.
* **`bugfix`** or **`fix`**: For resolving bugs or issues.

### 2. Description Formatting Rules
The `description` portion of your branch name must strictly adhere to these character rules:

* **Lowercase Only:** Use exclusively lowercase letters (`a-z`) and digits (`0-9`).
* **Hyphen Separators:** Use hyphens (`-`) to separate words or segments.
* **Dots Permitted:** You may use dots (`.`) within segments (e.g., for version numbers like `v1.2`).
* **No Special Characters:** Do not use spaces, underscores (`_`), slashes (`/`), or uppercase letters.

### 3. Trunk Branches
The following branches are reserved as foundational trunk branches and should not be used as prefixes or created manually:
* `main`
* `master`
* `develop`

---

## Examples

**✅ Valid Branch Names:**
* `feat/add-flashcard-ui`
* `fix/auth-token-validation`
* `release/v1.0.0`

**❌ Invalid Branch Names:**
* `feature_add_ui` *(uses underscores instead of a slash and hyphens)*
* `Fix/Auth` *(contains uppercase letters)*
* `add-flashcard-ui` *(missing the type prefix)*
* `feat/add ui layout` *(contains spaces)*
