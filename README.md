# 🎬 AI Film Editor Agent
**A Local, Privacy-First AI Copilot for Video Post-Production**

> **Built on:** Ubuntu 24.04 LTS • **Powered by:** Llama 3, Faster-Whisper, FFmpeg • **Hardware:** NVIDIA RTX 4060

---

## 🚀 Project Resources (Submission Links)

| Resource | Description | Link |
| :--- | :--- | :--- |
| 📄 **Project Report** | Detailed technical report (Google Docs) | [**Click Here to View Report**](https://docs.google.com/document/d/1W8FbaQ_XdbbtzxByNswXwDqQvs_0aQWqFrVkVMZcJM8/edit?usp=sharing) |
| 📊 **Presentation** | Project slides (Google Slides) | [**Click Here to View PPT**](https://docs.google.com/presentation/d/1Pu3WVRpg4_vMTsy545VzuKtRHrf_6LsIHrIIwMIqxYc/edit?usp=sharing) |
| 🎥 **Demo Video** | Walkthrough of the agent in action | [**Click Here to Watch Demo**](https://drive.google.com/file/d/1mM2qeenwKuijmnVEF1ddXBey3agEe4ym/view?usp=sharing) |
| 📓 **Source Code** | Main logic notebook | [**AI_Film_Editor.ipynb**](./AI_Film_Editor.ipynb) |

---

## 🧐 Problem Statement
Post-production is the bottleneck of modern content creation. Editors waste hours on repetitive tasks:
1.  **"Rough Cuts":** Manually listening to footage to find and remove bad takes.
2.  **Color Grading:** Adjusting curves and levels for basic stylistic changes.

Existing solutions are either too complex (Premiere Pro) or cloud-based, which poses **privacy risks** for unreleased footage and incurs high costs.

## 💡 The Solution
The **AI Film Editor Agent** is a local Python application that allows users to edit video using **Natural Language**. It acts as a "Director's Assistant":
* **You say:** *"Remove the bad takes and make the video look cinematic and warm."*
* **The AI:** 1.  Uses **Llama 3** to understand your intent.
    2.  Uses **Whisper** to find your spoken "Cut Start" / "Film Start" markers.
    3.  Uses **FFmpeg** to physically chop the video and apply color filters.

---

## ✨ Key Features

### ✂️ Smart Cut Engine
* **Voice-Activated Editing:** The agent listens for specific keywords in the audio track.
* **Logic:**
    * Say **"Cut Start"** -> AI marks the beginning of a bad take.
    * Say **"Film Start"** -> AI marks the end of a bad take.
    * **Result:** The system automatically deletes the segment in between and stitches the good takes together.

### 🎨 Natural Language Color Grading
* **Text-to-Filter:** Translate abstract requests into complex FFmpeg filter graphs.
* **Supported Styles:**
    * *"Make it warm"* (Boosts Red/Yellow)
    * *"Make it cool"* (Boosts Blue/Cyan)
    * *"Make it black and white"* (Desaturates)
    * *"Brighten the video"* (Adjusts Exposure)

### 🔒 100% Local Privacy
* No video data leaves your machine.
* Runs entirely on local hardware (tested on RTX 4060).
* Zero API costs.

---

## ⚙️ System Architecture: "The Brain & The Hands"

1.  **User Input:** Natural Language Text.
2.  **The Brain (Llama 3):** Analyzes intent and outputs a strict **JSON Command**.
3.  **The Hands (Python Controller):** * Parses the JSON.
    * Calls **Faster-Whisper** for audio analysis.
    * Calls **FFmpeg** for video rendering.
4.  **Output:** A processed `.mp4` file.

---

## 🛠️ Installation & Setup

### Prerequisites
* Ubuntu 20.04/22.04/24.04 (Recommended)
* Python 3.10+
* NVIDIA GPU (Recommended for speed, but runs on CPU)
* [Ollama](https://ollama.com/) installed

### Step 1: Install System Dependencies
```bash
sudo apt update
sudo apt install ffmpeg python3-venv python3-dev build-essential
```
Step 2: Set up the AI Model (The Brain)

Install Ollama and pull the Llama 3 model:
```Bash

curl -fsSL [https://ollama.com/install.sh](https://ollama.com/install.sh) | sh
ollama pull llama3
```
Step 3: Install Python Libraries
Bash

# Clone the repo
```bash
git clone [https://github.com/YOUR_USERNAME/AI-Film-Editor-Agent.git](https://github.com/YOUR_USERNAME/AI-Film-Editor-Agent.git)
cd AI-Film-Editor-Agent
```
# Create virtual environment
```bash
python3 -m venv venv
source venv/bin/activate
```
# Install requirements
```bash
pip install -r requirements.txt
```


🚀 How to Run
Start the Brain: Open a terminal and run Ollama.
```bash
  ollama serve
```
Run the Agent: Open the Jupyter Notebook.
```bash
   jupyter lab
```
 Execute: Open AI_Film_Editor.ipynb, run all cells, and enter commands in the prompt.
    Plaintext

🎬 COMMAND THE AI: Run smart cut and make it look warm.

📊 Performance

Tested on NVIDIA GeForce RTX 4060:

    Inference Speed (Whisper): ~4 seconds for a 30s clip.

    LLM Latency: <1.5 seconds per request.

    VRAM Usage: ~6GB Peak.

📜 License

This project is open-source and available under the MIT License.
