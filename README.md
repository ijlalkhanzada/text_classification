<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FastAPI Sentiment Analysis API</title>
</head>
<body>

<h1>FastAPI Sentiment Analysis API</h1>

<p>This project provides a simple API for sentiment analysis using FastAPI and Hugging Face's <code>transformers</code> library. The API allows users to classify text sentiment through an HTTP endpoint.</p>

<h2>Features</h2>
<ul>
    <li><strong>Text Sentiment Classification</strong>: The API accepts text input and returns the sentiment (positive, negative, etc.) along with the confidence score.</li>
    <li><strong>CORS Support</strong>: Cross-Origin Resource Sharing (CORS) is enabled, allowing access from any origin.</li>
    <li><strong>Asynchronous Handling</strong>: The server is designed to handle multiple requests concurrently.</li>
    <li><strong>Model Used</strong>: The project leverages Hugging Face's pre-trained models for sentiment analysis (you can customize the model if needed).</li>
</ul>

<h2>Requirements</h2>
<p>To run the API locally, install the following libraries:</p>
<ul>
    <li><code>fastapi</code>: The web framework used for creating the API.</li>
    <li><code>uvicorn</code>: A lightweight ASGI server used to run FastAPI.</li>
    <li><code>transformers</code>: Hugging Face's library for pre-trained NLP models.</li>
    <li><code>torch</code>: Required for running models like BERT.</li>
    <li><code>nest_asyncio</code>: To handle event loop issues in Jupyter environments.</li>
</ul>

<p>Install the dependencies by running:</p>
<pre><code>pip install fastapi uvicorn transformers torch nest_asyncio</code></pre>

<h2>How to Run</h2>
<ol>
    <li>Clone the repository:
        <pre><code>git clone https://github.com/your-username/fastapi-sentiment-analysis.git
cd fastapi-sentiment-analysis</code></pre>
    </li>
    <li>Run the Python script in a Jupyter notebook or a standard Python environment.</li>
    <li>Once the server starts, it will be accessible at <code>http://0.0.0.0:8000</code>.</li>
</ol>

<h2>Usage</h2>
<p>To classify the sentiment of a given text, send a <code>GET</code> request to the <code>/classify/{text}</code> endpoint.</p>

<p>Example request:</p>
<pre><code>http://0.0.0.0:8000/classify/I love this product!</code></pre>

<p>Example response:</p>
<pre><code>{
  "label": "POSITIVE",
  "score": 0.9998
}</code></pre>

<h2>Customization</h2>
<ul>
    <li><strong>Changing the Model</strong>: You can modify the model used by changing the <code>pipeline()</code> call in the script. For example, if you want to use a different task like text classification, you can adjust the pipeline as needed:
        <pre><code>classifier = pipeline('text-classification')</code></pre>
    </li>
    <li><strong>Port Change</strong>: You can change the server port by modifying the <code>uvicorn.run()</code> parameters in the <code>run_server</code> function.</li>
</ul>

<h2>Running on Jupyter</h2>
<p>If you're running this API inside a Jupyter Notebook, the <code>nest_asyncio</code> library is used to avoid issues with event loops. It allows you to run the server without encountering conflicts.</p>

<h2>License</h2>
<p>This project is licensed under the MIT License. See the <code>LICENSE</code> file for details.</p>

</body>
</html>
