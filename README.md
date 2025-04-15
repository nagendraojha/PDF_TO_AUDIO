# PDF_TO_AUDIO
1. Library Imports:
Tkinter: Used to create the graphical user interface (GUI) where you can interact with the program.

filedialog: For selecting the PDF file using a file dialog.

pyttsx3: A Python library for text-to-speech (TTS) conversion. It allows you to speak the text extracted from the PDF.

PyPDF2 (PdfReader): To read the contents of the PDF file and extract the text from it.

threading: To allow the text-to-speech reading to happen in a separate thread, ensuring that the GUI remains responsive while reading.

2. GUI Setup:
Buttons:

Start Button: Starts reading the PDF aloud when clicked.

Stop Button: Stops the reading process when clicked.

Select PDF Button: Opens a file dialog to choose the PDF you want to read aloud.

Speed Slider: Adjusts the speed of speech dynamically, allowing you to control how fast or slow the text is read.

Voice Selection Radio Buttons: Allows the user to choose between a male or female voice for reading the PDF text aloud.

3. Speech Settings:
Pyttsx3 Engine Initialization: The pyttsx3.init() function initializes the text-to-speech engine.

Speech Rate Adjustment: The rate of speech is adjusted dynamically using the speed_slider value. The rate is set between 50 and 300.

Voice Selection: The available voices are fetched using self.speaker.getProperty('voices'). The user can select between a male or female voice. By default, the male voice is selected.

Male voice is typically the first in the list, and female voice is the second.

4. PDF Selection and Text Extraction:
Selecting a PDF: Clicking the "Select PDF" button opens a file dialog that allows you to select the PDF file you want to read.

Extracting Text: The extract_text_from_pdf() function extracts all text from the selected PDF using the PyPDF2 library. The text from each page is concatenated into one string.

5. Speech Functionality:
Starting the Reading: When the "Start" button is clicked, the program:

Extracts the text from the PDF.

Fetches the speech rate from the speed slider.

Fetches the voice selection (male/female).

Starts reading the PDF aloud using the pyttsx3 engine in a new thread (to keep the GUI responsive).

Stopping the Reading: Clicking the "Stop" button immediately stops the speech using self.speaker.stop().

6. Threading:
The reading of the PDF text is done in a separate thread using the threading.Thread class to avoid blocking the GUI. This ensures that while the text is being read aloud, the user can still interact with the interface (adjust speed, change voice, stop reading).

7. Error Handling:
No PDF Selected: If no PDF is selected and the user tries to start reading, a message is printed, and the reading does not start.

No Extracted Text: If the text extraction fails (empty PDF or no text), the program informs the user.

8. GUI Interaction Flow:
Select a PDF file: First, the user selects a PDF using the "Select PDF" button.

Adjust speed: The user can adjust the speech rate using the Adjust Speed slider.

Choose voice: The user can select either a Male or Female voice using the radio buttons.

Start reading: When the Start button is clicked, the text is extracted from the PDF and read aloud in the selected voice and speed.

Stop reading: The Stop button stops the speech if it is ongoing.

9. Mainloop:
The root.mainloop() is the main loop of the Tkinter GUI. This loop runs continuously, waiting for user input (button clicks, slider adjustments), and handles the interaction with the user.

Summary:
Functionality: This app reads aloud the text from a selected PDF file.

User Controls:

Start and Stop buttons to control the reading.

Speed slider to adjust the reading speed.

Voice selection (Male/Female) to choose the voice.

Threading ensures the GUI stays responsive while reading.

The app uses pyttsx3 for speech synthesis and PyPDF2 to extract text from the PDF.
