News Authenticity Checker Web Application
This is a basic web application, which can be deployed in Google Colab, that labels news headlines or articles as REAL or FAKE based on a pre-trained machine learning model.

Project Overview
The tool employs a TF-IDF vectorizer and a Multinomial Naive Bayes classifier that has been trained using a dataset comprising real and forged news. It offers an easy-to-use web interface developed with Flask where one can submit text and get a real-time prediction. Deployment is mostly done using Google Colab, where `ngrok` is utilized to generate a public URL for the Flask app.

Files in this Repository
*   "news_classifier_app.ipynb": The primary Google Colab notebook with the Python code for the Flask web app, model loading, text preprocessing, and prediction process.
*   "news_model.pkl": The pre-trained Scikit-learn Multinomial Naive Bayes classification model.
*   `vectorizer.pkl": The pre-trained Scikit-learn TF-IDF vectorizer.
*   "requirements.txt": (Optional) List of Python dependencies. The notebook installs these automatically.
*   "README.md": This document, with setup, deployment, and usage instructions.

Features
*   REAL/FAKE news text classification.
*   Plain and straightforward web interface.
*   Easy to deploy and run in Google Colab.
*   Uses NLTK for text preprocessing (lowercase, punctuation removal, stopwords removal).
*   Uses TF-IDF for feature extraction and Multinomial Naive Bayes model for classification.

How to Run (in Google Colab)
Prerequisites:
*   A Google Account (for Google Colab).
*   An ngrok account and authtoken (ngrok needs it for tunnel creation).

Setup and Execution Steps:

1.  Clone or Download this Repository:
    *   Get all files from this repository, so you have `news_classifier_app.ipynb`, `news_model.pkl`, and `vectorizer.pkl`.

2.  Open the Notebook in Colab:
    *   Open [Google Colab](https://colab.research.google.com/).
*   Choose `File > Upload notebook.` and upload the `news_classifier_app.ipynb` file.
    *   Alternatively, if this repository is public, you can open directly in Colab through `File > Open notebook > GitHub` tab, then type in the repository URL or search by username/repository.

3.  Set up ngrok Authtoken:
    *   Get your ngrok authtoken:
*   Register for a free account at [https://dashboard.ngrok.com/signup](https://dashboard.ngrok.com/signup).
        *   After logging in, locate your authtoken on the "Your Authtoken" page: [https://dashboard.ngrok.com/get-started/your-authtoken](https://dashboard.ngrok.com/get-started/your-authtoken).
    * Insert the authtoken into the Colab notebook:
*   Go to the Step 8 (running with ngrok) section in the notebook.
*   Find the line:
            ```python
            NGROK_AUTH_TOKEN = "YOUR_ACTUAL_NGROK_AUTHTOKEN_HERE"

        *   Replace `"YOUR_ACTUAL_NGROK_AUTHTOKEN_HERE"` with your **actual ngrok authtoken**.

4.  Upload Model and Vectorizer (if prompted):
    *   The Colab notebook is designed to automatically look for `news_model.pkl` and `vectorizer.pkl`.
*   If these files are not present in the root of your Colab environment when you execute the notebook, the script will ask you to upload them.
    *   When asked by the `files.upload()` dialog, choose and upload the `news_model.pkl` and `vectorizer.pkl` files from this repository.

5.  Run All Cells:
*   In the Colab menu, select `Runtime > Run all`.
    *   This will execute all cells in the notebook, which includes:
        *   Installing necessary Python packages (Flask, pyngrok, pandas, nltk, scikit-learn, joblib).
        *   Downloading NLTK stopwords.
*   Potentially prompting for file uploads (as per Step 4).
        *   Loading the pre-trained model and vectorizer.
        *   Starting the Flask web server.
*   To create a public `ngrok` tunnel for the Flask app.

6.  Access the Web Application:
    *   After the last cell (Step 8) has successfully executed, it will output a public URL like the following:
        ```
???? Your News Classifier Website is LIVE! ????
        ???? Access it here: https://<random-string>.ngrok.io
        ```
    *   Press this `ngrok.io` URL. It will launch the news classifier web application in your browser.

Using the Application
1.  After loading the web page, you will find a big text field.
2.  Paste or type in the news headline or article content you wish to classify.
3.  Press the "Analyze News" button.
4.  The page will reload, and the classification result (???? REAL news or ???? FAKE news) appears below the button, along with the provided text.

Example Fake News Snippets for Testing:
*   "BREAKING: Scientists Declare Chocolate Now Categorized as a Vegetable by WHO!"
*   "Leaked Memo: All Pigeons in Major Cities to Be Replaced by Surveillance Drones Next Year!"
    *   *(Expected Classification: FAKE)*

Example Real News Snippets for Testing:
*   "Central Bank Declares Quarter-Point Interest Rate Increase to Control Inflation."
*   "City Council Approves Budget for New Public Library Renovation Project."
    *   *(Expected Classification: REAL)*

 (Optional) Running Locally (For Advanced Users/Alternative Testing)

Though conceived for Colab, the underlying Flask app can be run locally if you have a local Python environment with Jupyter functionality (e.g., VS Code with Python extension, local Jupyter Lab/Notebook) and the necessary libraries installed.

1.  Make sure `news_model.pkl` and `vectorizer.pkl` are available in the same directory as the notebook.
2.  Install packages: `Flask`, `pyngrok` (not required if running locally), `pandas`, `nltk`, `scikit-learn`, `joblib`.
3.  Run the appropriate cells of the `.ipynb` file.
4.  The app should be available at `http://127.0.0.1:5000` in your web browser. The ngrok tunneling portion of the script might or might not work based on your local ngrok installation.
*For assessment according to project specifications, use the Google Colab approach outlined above.*

 Dependencies
The principal Python dependencies are:
*   Flask
*   pyngrok
*   pandas
*   nltk
*   scikit-learn
*   joblib
They are automatically installed while running the notebook within Colab.
