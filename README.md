<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
<<<<<<< HEAD
    <title>FastAPI Text Classification and Sentiment Analysis API</title>
=======
>>>>>>> 318bf74ddc58d7ce88d26b4299d082ab66634d1b
</head>
<body>

<h1>FastAPI Text Classification and Sentiment Analysis API</h1>

<p>This project provides a comprehensive <strong>text classification</strong> and <strong>sentiment analysis</strong> API using <strong>FastAPI</strong> and <strong>Hugging Face's transformers</strong> library, featuring pre-trained models like <strong>DistilBERT</strong>. The API allows users to classify text and determine its sentiment (e.g., positive, negative, neutral) through HTTP endpoints.</p>

<h2>Key Features</h2>
<ul>
    <li><strong>Text Classification</strong>: The API classifies input text into predefined categories (sentiment analysis, news categories, etc.).</li>
    <li><strong>Sentiment Analysis</strong>: It analyzes input text to determine the sentiment as positive, negative, or neutral, and provides a confidence score.</li>
    <li><strong>CORS Enabled</strong>: The API is accessible from any origin due to CORS support.</li>
    <li><strong>Asynchronous Processing</strong>: It handles multiple requests concurrently for efficient performance.</li>
    <li><strong>Pre-trained Models</strong>: Supports various Hugging Face pre-trained models such as <code>distilbert-base-uncased</code>.</li>
</ul>

<h2>Requirements</h2>
<p>To set up and run the API locally, install the following dependencies:</p>
<pre><code>pip install fastapi uvicorn transformers torch nest_asyncio</code></pre>

<h3>Dependencies Overview</h3>
<ul>
    <li><code>FastAPI</code>: Web framework for building APIs.</li>
    <li><code>Uvicorn</code>: ASGI server to run the FastAPI app.</li>
    <li><code>Transformers</code>: Hugging Face's library for NLP tasks and pre-trained models.</li>
    <li><code>Torch</code>: Required for running models like DistilBERT.</li>
    <li><code>Nest Asyncio</code>: Used to handle event loops in Jupyter environments.</li>
</ul>

<h2>How to Run the API</h2>
<ol>
    <li><strong>Clone the repository</strong>:
        <pre><code>git clone https://github.com/your-username/text-classification-fastapi.git
cd text-classification-fastapi</code></pre>
    </li>
    <li><strong>Run the API</strong> in a Python environment or a Jupyter Notebook:
        <pre><code>uvicorn main:app --reload</code></pre>
        If running in a Jupyter Notebook, use <code>nest_asyncio</code> to avoid event loop conflicts:
        <pre><code>import nest_asyncio
nest_asyncio.apply()</code></pre>
    </li>
    <li>Access the API at <code>http://0.0.0.0:8000</code>.</li>
</ol>

<h2>API Endpoints</h2>

<h3>1. Sentiment Analysis (<code>/classify/{text}</code>)</h3>
<ul>
    <li><strong>Method</strong>: <code>GET</code></li>
    <li><strong>Description</strong>: Takes an input string and classifies the sentiment of the text.</li>
    <li><strong>Response</strong>:
        <ul>
            <li><code>category</code>: The predicted category (e.g., POSITIVE, NEGATIVE, NEUTRAL).</li>
            <li><code>confidence</code>: The confidence score for the classification.</li>
        </ul>
    </li>
</ul>

<h4>Example Request</h4>
<pre><code>GET http://0.0.0.0:8000/classify/I love this product!</code></pre>

<h4>Example Response</h4>
<pre><code>{
  "category": "POSITIVE",
  "confidence": 0.9998,
  "message": "The model is highly confident that the input text belongs to the category 'POSITIVE', with a confidence score of 0.9998."
}</code></pre>

<h2>Customization Options</h2>
<ul>
    <li><strong>Model Selection</strong>: Change the pre-trained model for text classification by updating the <code>pipeline()</code> call in the Python script:
        <pre><code>classifier = pipeline('text-classification', model='your-preferred-model')</code></pre>
    </li>
    <li><strong>Port Configuration</strong>: Modify the port on which the FastAPI server runs by changing the <code>uvicorn.run()</code> function:
        <pre><code>uvicorn.run(app, host="0.0.0.0", port=your-port)</code></pre>
    </li>
</ul>

<h2>Example HTML Frontend</h2>
<p>If you want to create a simple HTML frontend to interact with the API, here is a basic example:</p>

<pre><code>&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="UTF-8"&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
    &lt;title&gt;Text Classification Demo&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
    &lt;h1&gt;Text Classification API Demo&lt;/h1&gt;
    &lt;input type="text" id="inputText" placeholder="Enter text"&gt;
    &lt;button onclick="classifyText()"&gt;Classify&lt;/button&gt;
    &lt;p id="output"&gt;&lt;/p&gt;

    &lt;script&gt;
        async function classifyText() {
            const text = document.getElementById('inputText').value;
            const response = await fetch(`http://localhost:8000/classify/${encodeURIComponent(text)}`);
            const data = await response.json();
            document.getElementById('output').textContent = `Category: ${data.category}, Confidence: ${data.confidence}`;
        }
    &lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>

<h2>License</h2>
<p>This project is licensed under the MIT License. See the <code>LICENSE</code> file for more details.</p>

</body>
</html>
