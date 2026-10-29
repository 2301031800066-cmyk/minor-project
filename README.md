MetaForense — AI Crime Scene Analyser
MetaForense is a web-based prototype for exploring how AI-assisted image analysis could support a forensic investigation workflow. A user uploads a crime-scene image and selects a scene type. The app sends the image to an AI vision API and displays a structured, AI-generated interpretation, a possible event timeline, suggested evidence locations, potential tampering risks, a visual scene mock-up, an integrity-log demo, and a printable report.
Important limitation: This is an educational prototype, not a validated forensic tool. AI output may be incorrect or speculative and must not be treated as proof, a verified timeline, or legal advice. Do not upload real, confidential, or personally identifiable evidence without proper authorization and a suitable data-handling review.

Features
- Upload a JPG, PNG, WEBP, or GIF image.
- Select a scene type: indoor, outdoor, virtual/metaverse, vehicle, or staged scene.
- Request AI-generated findings, timeline, possible evidence locations, tampering risks, and an estimated time window.
- View a simple browser-based scene reconstruction mock-up and annotations.
- Review a chain-of-custody/integrity-log demonstration.
- Generate and print a report from the displayed analysis.
Technologies used
- HTML5 for page structure.
- CSS3 for the dark dashboard layout and styling.
- JavaScript for image upload, UI interactions, rendering, and report export.
- Python + Flask for a small local backend.
- Requests to call the Anthropic Messages API.
- Anthropic vision model for image interpretation (requires your own API key).
Project files
MetaForense/
├── index.html       # Frontend dashboard
├── app.py           # Flask backend; keeps the API key on the server
├── requirements.txt # Python dependencies
├── .env.example     # Example environment configuration
├── .gitignore       # Excludes secrets and Python cache files
└── README.md        # Project documentation
Requirements
- Python 3.10 or newer recommended.
- An Anthropic API account and API key with access to the configured model.
- Internet access for the AI API call and (optionally) Google Fonts.
Setup and run on Windows
1. Open the project folder
Extract the project ZIP, then open the MetaForense folder.
2. Open Command Prompt in this folder
In File Explorer, open the project folder, click the address bar, type cmd, and press Enter.
3. Create and activate a virtual environment (recommended)
py -m venv .venv
.venv\Scripts\activate
If py is not available, try python instead.
4. Install dependencies
python -m pip install -r requirements.txt
5. Configure the API key
Copy .env.example and name the copy .env. Open .env in a text editor and replace the placeholder with your own Anthropic API key:
ANTHROPIC_API_KEY=your_real_api_key_here
ANTHROPIC_MODEL=claude-sonnet-4-6
PORT=5000
Keep .env private. **Never commit it to GitHub** or share your API key in screenshots or reports. The .gitignore` file excludes it from Git.
6. Start the app
python app.py
Open this address in your browser:
http://127.0.0.1:5000
Keep the Command Prompt window open while using the app. To stop the server, press Ctrl+C.
How to use
1. Open the local app in your browser.
2. Upload a test image that you are permitted to use.
3. Choose the relevant scene type.
4. Select Analyse Crime Scene and wait for the API response.
5. Review the Analysis, VR Scene, Blockchain/Integrity, and Report tabs.
6. Use Export in the Report tab to open the browser print dialog. From there, choose a printer or “Save as PDF”.
Dataset
The supplied HTML file does not identify or include a dataset. The prototype works with an image uploaded by the user, so no fixed dataset is bundled. If your assignment requires a dataset, add the actual dataset name and its official URL here after selecting one. Do not claim a dataset was used unless you really used it.
Important implementation notes
- The API key is read by app.py from the local .env file; it is not placed in the browser JavaScript.
- The current “VR” view is a 2D visual mock-up, not a true 3D/VR reconstruction.
- The integrity/chain-of-custody panel is a simulation. It does not connect to Ethereum, write blockchain transactions, or provide a legally validated chain of custody. Hash/transaction-like strings in the original prototype should not be represented as verified blockchain records.
- The AI-generated incident description, confidence, time window, evidence suggestions, and tampering risks are hypotheses generated from an image. They are not independently verified forensic findings.
- This demo has no user login, database, case-management system, or production-grade privacy controls.
- The configured model name may need to be changed in .env if your Anthropic account does not have access to it.
Troubleshooting
ANTHROPIC_API_KEY is not set
- Ensure the file is named .env (not .env.txt) and is in the same folder as app.py.
- Check that the key line has no extra quotes or spaces around the key.
Authentication or model error
- Confirm your API key is active, billing is configured if required, and your account has access to the model named in ANTHROPIC_MODEL.
Port 5000 is already in use
- Set PORT=5001 in .env, restart python app.py, and open http://127.0.0.1:5001.
The browser says the site cannot be reached
- Make sure python app.py is still running and that you opened the local address shown above, not the original file:///... path.
