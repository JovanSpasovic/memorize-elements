# Element List Memorization App

A lightweight, browser-based tool for memorizing ordered or unordered lists (e.g., periodic table elements, vocabulary) using three modes: Drag-and-Drop, Typing, and List. Upload `.txt` files with numbered items (e.g., `1. Hydrogen`) for ordered lists or plain names (e.g., `Hydrogen`) for unordered lists. The app automatically selects Typing mode for ordered lists and List mode for unordered lists, with the option to switch modes. Practice arranging, typing, or recalling items, and analyze errors with a detailed overlay. No login or server dependencies—just HTML, JavaScript, and Tailwind CSS.

## Features

- **Tri-Mode Practice**:
  - **Drag-and-Drop**: Drag shuffled items to match numbered positions (ordered lists: file numbers; unordered: assigned 1, 2, 3, ...).
  - **Typing**: Type item names in order next to numbers (ordered: file order; unordered: assigned order).
  - **List**: Type all items in any order in a textarea, seeing only the file name (e.g., `elements.txt`).
- **Automatic Mode Detection**:
  - Ordered lists (`NUMBER. NAME`, e.g., `1. Sodium`): Default to Typing mode.
  - Unordered lists (plain `NAME`, e.g., `Sodium`): Default to List mode.
  - Switch modes via dropdown for flexibility.
- **Custom File Upload**: Load `.txt` files with `NUMBER. NAME` (ordered) or `NAME` (unordered) formats.
- **Compact Layout**: 48px number column with height-aligned (`h-12`) elements/inputs for Drag-and-Drop/Typing modes.
- **Error Analysis**: After an incorrect “Check Answers”, a button appears to show an overlay:
  - Ordered lists: Correct order (green) vs. your answers (green/red) with numbers.
  - Unordered lists: Correct items (green) vs. your answers (green/red, sorted, with “missing” for omitted items).
- **Unbiased Randomization**: Fisher-Yates shuffle for varied item order in Drag-and-Drop mode.
- **Instant Feedback**: “Check Answers” verifies correctness; “Reset” reshuffles or clears inputs.
- **No Dependencies**: Runs in modern browsers using Tailwind CSS via CDN.

## Setup

1. **Download**:
   - Save the `index.html` file from this repository.
2. **Run**:
   - Open `index.html` in a modern browser (e.g., Chrome, Firefox, Safari).
   - No server or installation required; everything runs client-side.

## Usage

### 1. Prepare a `.txt` File
Create a text file in one of two formats:
- **Ordered List** (defaults to Typing mode):
  ```
  1. Sodium
  2. Magnesium
  3. Aluminum
  4. Silicon
  ```
  Save as `elements_ordered.txt`.
- **Unordered List** (defaults to List mode):
  ```
  Sodium
  Magnesium
  Aluminum
  Silicon
  ```
  Save as `elements_unordered.txt`.

Alternatively, use the default ordered list (Hydrogen to Neon, Typing mode).

### 2. Load a List
- **Upload File**: Click the file input to select a `.txt` file:
  - Ordered (`NUMBER. NAME`): Loads in Typing mode, showing numbered inputs.
  - Unordered (`NAME`): Loads in List mode, showing the file name and textarea.
- **Default List**: If no file is uploaded, practice with the built-in periodic table list (ordered, Typing mode).

### 3. Choose a Mode
- **Mode Dropdown** (above the list):
  - **Drag-and-Drop**: Items appear shuffled; drag to align with numbers (e.g., “Sodium” to `1.` for ordered, or assigned numbers for unordered).
  - **Typing**: Input fields appear; type names in order (e.g., “Sodium” next to `1.`).
  - **List**: Shows the file name (e.g., `elements.txt`) and a textarea; type all items in any order (e.g., “Magnesium\nSodium”).
- The app auto-selects Typing for ordered lists or List for unordered lists, but you can switch modes.

### 4. Practice
- **Interact**:
  - **Drag-and-Drop**: Drag items to their correct positions.
  - **Typing**: Enter names (case-insensitive, e.g., “sodium” matches “Sodium”).
  - **List**: Type items, one per line, in any order (e.g., “Silicon\nSodium\nAluminum\nMagnesium”).
- **Check Answers**: Click the blue “Check Answers” button:
  - Correct: “Correct! Great job!” (green).
  - Incorrect: “Incorrect. Try again!” (red), and the yellow “Error Analysis” button appears.
  - List mode: Correct if all items match, regardless of order.
  - Typing/Drag-and-Drop: Correct if order matches (file numbers or assigned).
- **Error Analysis**:
  - If incorrect, click “Error Analysis” to view an overlay:
    - **Ordered Lists**: Correct order with numbers (green) vs. your answers (green/red).
    - **Unordered Lists**: Sorted correct items (green) vs. your answers (green/red, with “(missing)” for omitted items).
    - **List Mode**: Shows items only, sorted, without numbers.
    - Click “Close” to dismiss.
- **Reset**: Click the gray “Reset” button to reshuffle (Drag-and-Drop), clear inputs (Typing), or clear the textarea (List). Hides “Error Analysis”.

### 5. Learning Tips
- **Ordered Lists**:
  - Use Typing to master specific order, Drag-and-Drop for visual practice, and List for free recall.
  - Example: Memorize periodic table positions (e.g., `1. Hydrogen`).
- **Unordered Lists**:
  - Start with List to recall all items, then Typing/Drag-and-Drop to practice with assigned order (1, 2, 3, ...).
  - Example: Learn a set of vocabulary words without sequence.
- **Error Analysis**: Focus on red entries (incorrect or missing) to improve.
- **Mnemonics**: Use memory aids (e.g., “Happy Henry” for periodic table) for ordered lists.
- **Practice Daily**: Spend 5–10 minutes, rotating modes, for best retention.

## Example `.txt` Files
- **Ordered List** (`elements_ordered.txt`):
  ```
  1. Hydrogen
  2. Helium
  3. Lithium
  4. Beryllium
  5. Boron
  ```
- **Unordered List** (`elements_unordered.txt`):
  ```
  Hydrogen
  Helium
  Lithium
  Beryllium
  Boron
  ```
Save and upload via the file input.

## Customization
- **Default List**: Edit the `defaultElements` array in `index.html`’s `<script>`:
  ```javascript
  const defaultElements = [
    { name: "Sodium", order: 1 },
    { name: "Magnesium", order: 2 },
    { name: "Aluminum", order: 3 }
  ];
  ```
  This is treated as an ordered list (Typing mode).
- **Unordered Default**: Set `defaultElements` without numbers and update `isOrderedList = false`, `currentMode = "list"`.
- **Styling**: Modify Tailwind classes (e.g., change `bg-yellow-500` for “Error Analysis” to `bg-orange-500`).
- **Long Lists**: Overlay is scrollable; add `overflow-y-auto` to `order-container` for main UI scrolling.

## Limitations
- **File Formats**:
  - Ordered: Must be `NUMBER. NAME` (e.g., `1. Sodium`).
  - Unordered: Plain `NAME` (e.g., `Sodium`). Mixed formats default to unordered.
  - Invalid files revert to the default ordered list.
- **Typing/List Modes**: Require exact spelling (case-insensitive). Empty inputs/lines are “(empty)” in red.
- **List Mode**: Duplicates in answers may appear red if extra.
- **List Length**: Best for ~20 items. Overlay is scrollable, but main UI may need scrolling for long lists.
- **Assigned Orders**: Unordered lists use 1, 2, 3, ... in Typing/Drag-and-Drop, which may feel arbitrary.
- **Browser Compatibility**: Works in modern browsers; older browsers (e.g., IE) may not support Tailwind or drag-and-drop.

## Contributing
Fork this repository and submit pull requests for enhancements, such as:
- Progress tracking for correct attempts.
- Hint button to reveal items briefly.
- Autocomplete for Typing/List modes.
- Enhanced styling or React-based UI.

## License
MIT License. Use, modify, and distribute freely, with attribution.

## Acknowledgments
Built for flexible memorization, supporting both ordered and unordered lists. Powered by Tailwind CSS, JavaScript’s drag-and-drop API, and smart file format detection.

---
Happy memorizing! For issues or feature requests, open a GitHub issue or contact the maintainer.
