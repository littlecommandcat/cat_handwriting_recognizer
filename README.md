# Cat Handwriting Recognizer

A simple Python module for recognizing handwritten using machine learning. Designed for easy integration and efficient preprocessing.

## Features

- Preprocess handwritten images
- Extract simple features for recognition
- K-Nearest Neighbors (KNN) prediction
- Async support for building templates
- Timeout mechanism for long-running operations
- Save and load models as .npz files

## Installation

Install from PyPI:

```bash
pip install cat-handwriting-recognizer
```

Install from GitHub:

```bash
pip install git+https://github.com/littlecommandcat/cat_handwriting_recognizer.git
```

## Quick Example
```py
from cat_handwriting_recognizer import HandwritingRecognizer  
import asyncio

machine = HandwritingRecognizer(timeout=-1)

# Build templates from data
asyncio.run(machine.build_all_templates("directory")) # Your data directory

# Save model
machine.save_model("model.npz") # Save model file(.npz)

# Load model
machine.load_model("model.npz") # Load model file(.npz)

# Predict a picture
result = asyncio.run(machine.predict("file.png")) # Use model to predict png/jpg/jpeg file
print(result)
```
## Requirements

- Python 3.10+
- NumPy
- Pillow

## License

MIT License

## Author

littlecommandcat

# Changelog

## [1.2.5]
**Enhancements & Refactoring**
- Introduced **model merging functionality**, allowing multiple template models to be combined seamlessly.
- Added configurable **error-catching behavior**, enabling users to control whether exceptions are automatically handled.
- **Removed `timeout` attribute** and `self._timeout`, simplifying the class initialization and reducing internal state complexity.
- Improved internal consistency and robustness when handling multiple model inputs.

## [1.2.4]
**New Features & Improvements**
- Added **decorators for error catching and runtime checking**, enhancing stability during execution.
- Introduced several **custom error classes** to provide more granular exception handling, covering model operations, feature extraction, and predictions.
- Added a **`timeout` parameter** to allow users to set execution limits for long-running operations.
- Fixed **issues with overwriting previously loaded models**, ensuring that templates are preserved correctly after loading or inputting new models.

## [1.2.3]
**Bug Fixes**
- Resolved `ModuleNotFoundError` and **import-related issues**, ensuring smoother package integration.
- Fixed initialization problems that prevented proper loading of models and internal state setup.

## [1.2.2]
**Maintenance**
- Minor internal fixes and adjustments to package metadata and structure.

## [1.2.1]
**Initial Stable Release**
- First stable release with core functionality:
  - Handwriting image preprocessing
  - Feature extraction
  - KNN-based prediction
  - Model saving and loading