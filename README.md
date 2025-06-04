What This Project Does
This Gradio-based bot:
Accepts natural language questions from users in any language.
Uses language detection and translation to handle the multilingual input.

It can:
Predict a suitable crop for farming based on the current weather (temperature + humidity).
Answer weather-related questions.
Disambiguate words like "plant" (crop vs. factory) using WSD (Word Sense Disambiguation).
Support NER (Named Entity Recognition) to extract city names.

Technologies and Libraries Used:

Feature	Library Used

Multilingual Translation	   deep_translator (GoogleTranslator)
Language Detection	         deep_translator.single_detection()
NER (Location extraction)	   transformers pipeline with BERT-based NER
WSD (Word Sense Disambig.)	 sentence-transformers for semantic similarity
Crop Prediction              RandomForestClassifier from sklearn
Weather Data API	           OpenWeatherMap (requests)
UI	                         gradio

Pipeline Summary: 
User asks a question in any language.
Text is translated to English.
NER model extracts city name from the question.
Weather data (temperature, humidity) for the city is fetched using OpenWeather API.
If the question is crop-related:
A trained RandomForestClassifier predicts the best crop.
If the question is ambiguous (e.g., "spray"), the bot uses WSD to clarify meaning.
Final answer is translated back into the user's original language.
Response is displayed via Gradio.


Warnings & Suggestions: 
You’re seeing a few warnings, which aren’t breaking the code but worth addressing:

Tqdm + Jupyter Warning: Update Jupyter + ipywidgets to fix:
pip install -U jupyter ipywidgets

Optree Warning: Update optree for PyTorch compatibility:
pip install --upgrade 'optree>=0.13.0'

Sklearn Warning: Feature names mismatch. Fix this by passing a DataFrame with column names instead of a raw NumPy array:
input_data = pd.DataFrame([[temp, humidity]], columns=["temperature", "humidity"])
