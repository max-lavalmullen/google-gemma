# Local Gemma Model Guide

This folder contains everything you need to run Google's Gemma models locally on your Mac using the `llama.cpp` engine.

## 🚀 Quick Start (Recommended)
We have created a simple launcher script to make running models easy. You can run it from the terminal or just **double-click** the file in Finder.

Usage: `./run-gemma [mode]`

*   **Interactive Menu:** `./run-gemma` (or Double-Click)
*   **General Assistant:** `./run-gemma gen`
*   **Programmer:**      `./run-gemma code`
*   **Translator:**      `./run-gemma trans`
*   **Doctor:**          `./run-gemma med`

---

## 1. The "Engine"
*   **Folder:** `llama.cpp/`
    *   This is the software that actually runs the models. It's a high-performance C++ engine compiled specifically for your Mac's Apple Silicon (Metal/GPU).

## 2. The Models (The "Brains")
You have a collection of specialized "GGUF" model files. Each one is a specialist in a different field.

### A. The General Assistant (Gemma 3)
*   **File:** `google_gemma-3-12b-it-qat-Q6_K_L.gguf`
*   **Role:** Your daily driver. Creative writing, general questions, brainstorming.
*   **Manual Command:**
    ```bash
    ./llama.cpp/build/bin/llama-cli -m google_gemma-3-12b-it-qat-Q6_K_L.gguf -ngl 99 -c 8192 -cnv --color on
    ```

### B. The Programmer (CodeGemma 1.1)
*   **File:** `codegemma-1.1-7b-it-Q6_K.gguf`
*   **Role:** Writing Python/JS/C++ code, debugging, explaining programming concepts.
*   **Manual Command:**
    ```bash
    ./llama.cpp/build/bin/llama-cli -m codegemma-1.1-7b-it-Q6_K.gguf -ngl 99 -c 8192 -cnv --color on
    ```

### C. The Translator (TranslateGemma)
*   **File:** `translategemma-12b-it.Q6_K.gguf`
*   **Role:** High-accuracy translation between languages.
*   **Manual Command:**
    ```bash
    ./llama.cpp/build/bin/llama-cli -m translategemma-12b-it.Q6_K.gguf -ngl 99 -c 8192 -cnv --color on
    ```

### D. The Doctor (MedGemma 1.5)
*   **File:** `medgemma-1.5-4b-it-Q8_0.gguf`
*   **Role:** Medical research, understanding clinical terms, biology questions.
*   **Note:** This is a smaller 4B model but at "Q8" (Max) precision for accuracy. *Not for real medical advice.*
*   **Manual Command:**
    ```bash
    ./llama.cpp/build/bin/llama-cli -m medgemma-1.5-4b-it-Q8_0.gguf -ngl 99 -c 8192 -cnv --color on
    ```

## Command Explanations
*   `-m [file]`: Selects the model file to load.
*   `-ngl 99`: "n-gpu-layers". Tells your Mac to put 100% of the work on the GPU for speed.
*   `-c 8192`: Context window. The model can remember about 6,000 words.
*   `-cnv`: Conversation mode. Enables the chat interface.
*   `--color on`: Makes the output text easier to read.
