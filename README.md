# PlainSpeak-Llama
Fine-tuning Llama-3 to translate Medical, Legal, and Academic complexity into clear, human-readable language.
# 🧠 PlainSpeak-Llama: Jargon to ELI5 Converter

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1wRhvhxNqchYNV4_pNsRz8J-xrkW-_mgo?usp=sharing)
[![Powered by Unsloth](https://img.shields.io/badge/Powered%20by-Unsloth-FF5733)](https://github.com/unslothai/unsloth)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**PlainSpeak-Llama** is a fine-tuned LLM designed to translate complex technical jargon (Medical, Legal, and Academic) into clear, simple English ("Explain Like I'm 5"). 

Built using **Llama-3-8b**, **Unsloth**, and **LoRA** adapters.

---

## 🎥 Demo
![Demo Preview](https://s2.ezgif.com/tmp/ezgif-29a5d978fe13ed81.gif)

### Before & After Examples

| Domain | ❌ Complex Input | ✅ PlainSpeak Output (ELI5) |
| :--- | :--- | :--- |
| **Medical** | "Auscultation of the thorax revealed bilateral wheezing suggestive of acute bronchitis." | "Listening to the chest showed whistling sounds, which sounds like a bad chest cold." |
| **Legal** | "The Lessee shall be liable for any damages beyond reasonable wear and tear." | "If you rent this and break it, you have to pay. Small scratches from normal use are okay." |
| **Academic** | "The implementation utilizes a recursive neural network topology to optimize descent." | "The computer program uses a brain-like loop to learn math problems much faster." |

---

## 🚀 Features
*   **Domain Specific:** Trained on a curated dataset of Medical reports, Legal contracts, and Research abstracts.
*   **Efficient Training:** Uses **Unsloth** for 2x faster training and 60% less memory usage.
*   **4-Bit Quantization:** Runs on free Google Colab GPUs (Tesla T4).
*   **Gradio UI:** Includes a built-in web interface for real-time testing.

---

## 🛠️ How to Run (Free GPU)

You can run the full training and inference pipeline entirely in your browser using Google Colab.

1.  **Click the badge** at the top of this README.
2.  **Connect to GPU:** Go to `Runtime` > `Change runtime type` > Select `T4 GPU`.
3.  **Upload Data:** Upload the provided `train.jsonl` file to the Colab files section.
4.  **Run All:** Execute the cells to fine-tune the model and launch the Gradio app.

---

## 🔧 Technical Details

*   **Base Model:** `unsloth/llama-3-8b-bnb-4bit`
*   **Fine-Tuning Method:** LoRA (Low-Rank Adaptation)
    *   *Rank (r):* 16
    *   *Alpha:* 16
    *   *Target Modules:* q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj
*   **Inference Parameters:**
    *   *Repetition Penalty:* 1.1 (Prevents looping)
    *   *Max Tokens:* 128

---

## 📊 Dataset Generation
The dataset (`train.jsonl`) consists of 50 high-quality pairs generated synthetically. It follows the **Alpaca** format:

```json
{
    "instruction": "Simplify this text.",
    "input": "Myocardial infarction was ruled out...",
    "output": "It wasn't a heart attack."
}
```

---

## 🤝 Credits
*   **Unsloth AI** for the optimized training pipeline.
*   **Meta** for the Llama-3 model.
*   **Hugging Face** for the TRL and PEFT libraries.

---

*Created by Ali Khan*
