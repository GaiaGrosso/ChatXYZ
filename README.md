# ChatJesseT

## Usage

1. `requirements_test.txt` contains the full python environment used for development and testing. `requirements.txt` contains the more minimal version for deploying the Flask app. Set up a Python environment accordingly.

2. Set the OpenAI key (for embedding and chat completion calls):
```
export OPENAI_API_KEY="sk-xxx..."
```

3. Set a system prompt at `data/db/system_prompt.txt` and a context prompt at `data/db/context_prompt.txt`. The former will guide the general characteristics of the chatbot, while the later will give a stronger immediate signal.

4. To create text chunks and embeddings, run [`notebooks/01_data_collection.ipynb`](notebooks/01_data_collection.ipynb) and [`notebooks/02_embedding.ipynb`](notebooks/02_embedding.ipynb).

5. For local testing, simply do
```
python main.py
```
and navigate to `http://127.0.0.1:8080/`.

6. Deploy website through the Google App Engine with
```
gcloud app deploy
```
and navigate to the remote URL via
```
gcloud app browse
```
See [here](https://cloud.google.com/appengine/docs/standard/python3/runtime) for preliminary steps necessary for Google Cloud / App Engine deployment. For [here](https://cloud.google.com/docs/authentication/provide-credentials-adc#how-to) for initializing GOogle Cloud. Upload the text chunks and embeddings to Google Cloud for more efficient data loading; this can be done by manually uploading to the bucket specified in the `run()` function in [chatjesset.py](chatjesset.py). If loading text chunks and embeddings locally, uncomment the relevant lines in that file.
