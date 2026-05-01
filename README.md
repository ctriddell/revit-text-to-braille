# Revit Text to Braille (Dynamo)

A Dynamo script for Autodesk Revit that converts room names and numbers into Braille and generates corresponding Braille families placed directly in the model.
This tool is intended to support accessibility workflows by automating the creation of Braille signage geometry within Revit.

---

## 🚀 Features
- Converts standard text (room name + number) into Braille
- Automatically generates a Braille family per room
- Places the generated family at the room location
- Supports numbers with proper Braille number prefix
- Configurable spacing and scale (via script variables)

---

## 📦 Repository Contents
/dynamo
text_to_braille.dyn

/revit-family
Braille Template Family.rfa
Braille Dot.rfa

README.md
LICENSE

---

## ⚙️ Requirements
- Autodesk Revit (tested in version XX – update as needed)
- Dynamo (version X.X or later)
- Basic familiarity with running Dynamo scripts in Revit

---

## 🧠 How It Works

1. Collects all rooms in the model (option to filter by level)
2. Extracts:
   - Room Name
   - Room Number
3. Converts each character into Braille dot patterns
4. Generates dot geometry using a nested family approach:
   - `Braille Dot` → individual dot
   - `Braille Template Family` → container for generated layout
5. Saves a new family per room
6. Loads and places the family back into the project at the room location

---

## ▶️ Usage

1. Open your Revit project
2. Ensure the required families are available:
   - `Braille Template Family`
   - `Braille Dot`
3. Open Dynamo and load:

/dynamo/text_to_braille.dyn

4. Provide inputs:
- **Directory Path** → where generated families will be saved
- **All Levels (bool)** → process entire model or filter
- **Level (optional)** → specific level if filtering
5. Run the script

## 🔧 Configurable Parameters (in script)

```python
heightFactor = 0.250
letterSpacing = 0.125
````

* `heightFactor` → controls overall Braille scale
* `letterSpacing` → spacing between characters

---

## ⚠️ Notes & Limitations

* Currently supports:

  * Lowercase letters
  * Numbers (with number prefix)
* Does not yet support:

  * Punctuation
  * Grade 2 (contracted) Braille
* Family naming is based on:

  ```
  RoomName_RoomNumber.rfa
  ```
* Existing families with the same name will be overwritten

---

## 📁 Output

* A new `.rfa` file is created for each room
* Families are saved to the provided directory
* Families are automatically loaded and placed in the model

---

## 🐛 Error Handling

* Any failed rooms will be returned in the `errors` output
* Common issues:

  * Missing families
  * Invalid save directory
  * Unexpected room data

---

## 📌 Future Improvements

* UI inputs for scale and spacing
* Support for punctuation and symbols
* Grade 2 Braille support
* Option for single multi-room family instead of per-room files
* Better family reuse (avoid duplicates)

---

## 📄 License

This project is licensed under the MIT License. See `LICENSE` for details.

---

## 🤝 Contributing

Contributions, improvements, and suggestions are welcome.

If you find a bug or have an idea, feel free to open an issue or submit a pull request.

