## Bias Experimentation# Getting Started

To get started with this repository, follow these steps:

1. **Set up a Python virtual environment**: Create a new virtual environment using your preferred method (e.g., `python -m venv myenv` on Linux/macOS or `python -m venv myenv` on Windows).
2. **Activate the virtual environment**: Activate the virtual environment (e.g., `source myenv/bin/activate` on Linux/macOS or `myenv\Scripts\activate` on Windows).
3. **Install llama-cpp-python**: Install the `llama-cpp-python` package using pip. For Metal (Silicon Macs), use the following command: `CMAKE_ARGS="-DGGML_METAL=on" pip install llama-cpp-python`. For other systems, use `pip install llama-cpp-python`.

**Note**: The `llama-cpp-python` package is installed with Metal support on Silicon Macs to ensure compatibility with the M1 chip.

**Why this model?**

The model used in this repository was chosen because it is small enough to fit on an M1 Mac. However, your mileage may vary if you're using different models or are not CPU-constrained. The model's size was a key consideration to ensure it could run efficiently on the M1 chip.

**What's happening in the script?**

At a high level, the script loads a pre-trained language model and performs inference on input text. For more information, refer to the [link to relevant documentation or resources].
