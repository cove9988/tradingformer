# Project Title: LLM for Trading Application

## 1. Overview
Brief description of the project: To select, prepare data for, and outline the fine-tuning process for an LLM tailored to trading applications.

## 2. LLM Selection for Trading Tuning
- **Selected Model:** Mistral-7B-Instruct-v0.2
- **Reasoning:** Good balance of strong performance (reasoning, instruction following), manageable size (7 billion parameters) for fine-tuning on platforms like Google Colab (especially with QLoRA), active community support, and successful use as a base for domain-specific tuning.
- **Alternatives Considered:** Llama-2-7B/13B, Gemma-7B, other smaller Qwen models. These are also strong candidates but Mistral-7B-Instruct offers a very competitive edge in performance for its size.

## 3. Tuning Data Requirements
- **Format:** JSONL (JSON Lines), where each line is a JSON object.
- **Core Structure per JSON Object:**
  ```json
  {
    "instruction": "<Your trading-related question or task>",
    "input": "<Optional: context like market data, news, portfolio details>",
    "output": "<The desired, ideal response from the LLM>"
  }
  ```
- **Content Categories & Examples:**
  - **A. Market Analysis & Prediction:** (Instructions on analyzing trends, predicting movements, sentiment analysis using market data, technical indicators, news as input. Output should be the analysis/prediction.)
  - **B. Trading Strategy Generation & Explanation:** (Instructions to develop/explain strategies, risks, or generate trading code. Output is the strategy, explanation, or code.)
  - **C. Portfolio Management & Queries:** (Instructions on diversification, tax implications (with disclaimers), beta calculation using portfolio details as input. Output provides relevant information.)
  - **D. Order Execution & Terminology:** (Instructions to explain trading terms or scenarios. Output gives clear definitions/explanations.)
- **Data Quantity & Quality:** Aim for 500-1000+ high-quality, diverse, and accurate examples. Outputs should show reasoning and include disclaimers about not providing financial advice where appropriate.
- **Formatting for Training:** The SFTTrainer expects a single text field, typically formatted as: `<s>[INST] Instruction (plus Input if provided) [/INST] Output </s>`.

## 4. Tuning Script, Setup, and Steps (Google Colab Focus)
- **Libraries:** Hugging Face `transformers`, `peft` (for LoRA), `datasets`, `bitsandbytes` (for QLoRA), `trl` (for SFTTrainer).
- **Script Overview:** A Python script that performs the following:
  1. Loads the dataset (JSONL) and formats it into the required instruction-response structure.
  2. Loads the base model (Mistral-7B-Instruct-v0.2) with 4-bit quantization (QLoRA) and its tokenizer.
  3. Configures LoRA (Low-Rank Adaptation) for parameter-efficient fine-tuning.
  4. Sets up `TrainingArguments` for the SFTTrainer.
  5. Initializes the `SFTTrainer` with the model, tokenizer, dataset, and PEFT config.
  6. Runs the training loop.
  7. Saves the trained LoRA adapter.
  8. (Optional) Merges the adapter with the base model and saves the full model.
  9. (Optional) Includes a basic test pipeline.
- **Setup in Google Colab:**
  1. Open a new Colab notebook.
  2. Change runtime to GPU (T4 is usually available in free tier).
  3. Install libraries: `!pip install -q transformers datasets accelerate peft bitsandbytes trl`
  4. Upload `trading_data.jsonl` or mount Google Drive.
  5. (Optional) Login to Hugging Face Hub: `from huggingface_hub import notebook_login; notebook_login()`
- **Running the Tuning:**
  1. Paste the provided Python script into a Colab cell.
  2. Adjust parameters (model names, dataset path, epochs, batch size, LoRA config especially `target_modules`).
  3. Run the cell.
  4. Monitor training and save checkpoints to Google Drive.

## 5. Hardware Requirements (Google Colab Focus)
- **GPU:** NVIDIA T4 (16GB VRAM) is the minimum viable for 7B models with QLoRA. A100 (40GB+) or V100 (16/32GB) in Colab Pro are better.
- **RAM:** ~12GB (standard Colab) is generally sufficient for the script and data. High RAM option in Colab Pro is a plus.
- **Storage:** Use Google Drive for persistent storage of datasets, scripts, and model adapters/checkpoints. Session storage is temporary.
- **Key Techniques for Colab:** Utilize QLoRA, manage batch sizes carefully, use gradient checkpointing, and save work frequently to Google Drive.
