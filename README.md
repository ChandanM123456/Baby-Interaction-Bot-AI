# Baby-Interaction-Bot-AI
An experimental AI Baby Bot developed and designed to provide interactive entertainment and comfort to babies. It leverages webcam input for real-time mood analysis and microphone input for voice command recognition, offering a curated selection of songs, stories, and lullabies.

# Baby Interaction Bot AI

---

## Project Overview

This project presents an **experimental AI Baby Bot** designed to interact with infants (or adults simulating infant sounds/words) in a dynamic and responsive manner. The bot utilizes real-time webcam access for **facial emotion detection** and microphone input for **speech recognition (ASR)**. Based on the detected mood and vocalizations, the bot plays a curated selection of lullabies, rhymes, and stories, aiming to provide comforting or engaging content.

This project serves as a proof-of-concept for creating interactive AI companions for early childhood development, exploring the challenges and possibilities of real-time multi-modal interaction.

## Features

* **Real-time Facial Emotion Detection:** Analyzes live webcam feed to identify the baby's dominant emotion (e.g., happy, distressed, sleepy, neutral).
* **Speech Recognition (ASR):** Processes microphone input to attempt to transcribe vocalizations and recognize keywords like "story," "song," "mama," "papa," and basic vocabulary (using an adult-trained ASR model).
* **Mood-Based Content Selection:** Automatically suggests and plays appropriate lullabies (for sleepy/distressed moods), happy rhymes (for happy/engaged moods), or calming stories.
* **Interactive Dialogue:** Responds to recognized keywords and prompts for further interaction.
* **Multilingual Support (Basic):** Curated content and responses in both English and Hindi.

## Limitations & Important Notes

* **Baby Speech Recognition:** The ASR model currently implemented (`facebook/wav2vec2-base-960h`) is trained on adult speech. **It will struggle significantly with genuine infant babbling and indistinct vocalizations.** For effective interaction via voice, an adult needs to speak keywords (e.g., "story", "song", "mama", "कहानी") clearly and distinctly.
* **Real-time Performance:** Performance can vary based on system specifications (CPU/GPU) and microphone/webcam quality.
* **Content Placeholders:** The audio content URLs (`soundhelix.com` links) are placeholders. For a functional bot, you will need to replace these with direct links to publicly accessible MP3 or WAV files of actual lullabies, rhymes, and stories.
* **Internet Connection:** Required for gTTS (Text-to-Speech), ASR model downloads, and streaming audio content.

## Project Files

This repository contains the following Google Colab notebooks:

* **`Baby Interaction Bot.ipynb`**: This is the core bot implementation featuring real-time mood detection and voice recognition.
* **`BabyInterationBotWithDifferentLang.ipynb`**: This notebook likely explores or demonstrates the bot's functionality with different language content or features.

## Setup and How to Run in Google Colab

The easiest way to experience the Baby Interaction Bot is to run it directly in Google Colab.

1.  **Open in Google Colab:**
    * Click on either `Baby Interaction Bot.ipynb` or `BabyInterationBotWithDifferentLang.ipynb` within this GitHub repository.
    * On the notebook page, click the "Open in Colab" badge (usually near the top).
2.  **Run All Cells:** Once the notebook opens in Colab, go to `Runtime > Run all`.
3.  **Grant Permissions:** When prompted by your browser, **grant access to your Webcam and Microphone.** This is essential for the bot to function.
4.  **Wait for ASR Model Loading:** The bot will print "Loading ASR model... This may take a few minutes." Please be patient as the large language model downloads and initializes.
5.  **Interact:**
    * **Face:** Position the baby (or your face for testing) in front of the webcam. The bot will display the detected mood.
    * **Voice:** Speak clear keywords like "story," "song," "mama," "नमस्ते" into your microphone. Observe the "Baby Vocalization (ASR): 'TRANSCRIPTION HERE'" output to see what the bot's ASR is recognizing.

## Setup and How to Run Locally (Advanced)

Running this project locally is possible, but it requires a more involved setup due to the integration with browser-based webcam/microphone APIs (which Colab handles automatically with its JavaScript snippets).

**Important:** The current code is heavily reliant on Google Colab's unique environment (e.g., `google.colab.output`, `eval_js`). To run this purely locally as a standalone application, you would need to replace the JavaScript-based webcam/microphone capture and display parts with Python-native solutions (e.g., `cv2.VideoCapture` for webcam, `pyaudio` or `sounddevice` for microphone, and `matplotlib` or `cv2.imshow` for display).

If you are a developer comfortable with adapting code:

### 1. Prerequisites

* **Python 3.8+** installed on your system.
* **Git** installed (for cloning).
* **Internet Connection** for downloading models and content.
* A functioning **Webcam** and **Microphone**.
* **Jupyter Notebook** or **JupyterLab** installed (to run `.ipynb` files locally).
    ```bash
    pip install notebook  # or pip install jupyterlab
    ```

### 2. Download the Project

#### Option A: Download ZIP (Simplest)

1.  Go to the main page of the `Baby-Interaction-Bot-AI` GitHub repository.
2.  Click the green **`< > Code`** button.
3.  Select **"Download ZIP"**.
4.  Extract the downloaded ZIP file to a folder of your choice (e.g., `C:\Users\YourUser\Projects\BabyBotAI`).

#### Option B: Clone with Git (Recommended for Developers)

1.  Open your terminal or command prompt.
2.  Navigate to the directory where you want to save the project:
    ```bash
    cd C:\Users\YourUser\Projects\ # Or your preferred directory
    ```
3.  Clone the repository:
    ```bash
    git clone [https://github.com/ChandanM123456/Baby-Interaction-Bot-AI.git](https://github.com/ChandanM123456/Baby-Interaction-Bot-AI.git)
    ```
4.  Navigate into the cloned directory:
    ```bash
    cd Baby-Interaction-Bot-AI
    ```

### 3. Install Dependencies

Once you have the project files, you need to install the required Python libraries.

1.  Open your terminal or command prompt.
2.  Navigate to the project directory (if you're not already there):
    ```bash
    cd path/to/Baby-Interaction-Bot-AI
    ```
3.  Run the following command to install all necessary libraries:
    ```bash
    pip install ipywidgets==7.7.1 opencv-python-headless scikit-image pydub transformers scipy gTTS soundfile deepface torchaudio librosa notebook
    ```
    * **Note on `opencv-python-headless`**: For a standard desktop setup, `opencv-python` might be more common, but `opencv-python-headless` generally works fine too.
    * **Note on `ipywidgets`**: While included, some Colab-specific JavaScript interactions won't directly translate without further adaptations for a local Jupyter environment.

### 4. Run the Bot Locally

1.  Open your terminal or command prompt.
2.  Navigate to the project directory:
    ```bash
    cd path/to/Baby-Interaction-Bot-AI
    ```
3.  Start Jupyter Notebook:
    ```bash
    jupyter notebook
    ```
4.  Your browser will open to the Jupyter interface. Navigate to and open either `Baby Interaction Bot.ipynb` or `BabyInterationBotWithDifferentLang.ipynb`.
5.  Execute the cells in the notebook. Be aware that the JavaScript sections for camera/microphone access might require manual intervention or adaptation, as they are primarily written for the Colab environment.

## Technologies Used

* **Python 3**
* **Google Colab:** (Primary development environment)
* **OpenCV:** For facial detection and image processing.
* **DeepFace (Optional):** For advanced emotion analysis.
* **Hugging Face Transformers:** Specifically `Wav2Vec2ForCTC` and `Wav2Vec2Processor` for Automatic Speech Recognition.
* **Pydub:** For audio manipulation.
* **gTTS (Google Text-to-Speech):** For the bot's vocal responses.
* **IPython.display & google.colab.output:** Used for browser interaction within Colab.
