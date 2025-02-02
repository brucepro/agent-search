AgentSearch API Documentation
========================

Welcome to the AgentSearch API documentation. Here, you'll find a detailed guide on how to use the different endpoints provided by the AgentSearch service. This API allows you to interact with the powerful functionalities of the AgentSearch codebase and associated AI models.

Endpoint Overview
-----------------

1. **Search**: This endpoint allows you to fetch related search results for a given query. The results are powered by the AgentSearch framework and dataset.

Detailed Endpoint Descriptions
------------------------------

Search Endpoint
~~~~~~~~~~~~~~~

- **URL**: ``/search``
- **Method**: ``POST``
- **Description**: This endpoint interacts with the Retriever module of the AgentSearch-Infra codebase, allowing you to search for related documents based on the provided queries.

**Request Body**:
  - ``query``: A string that contains the query you wish to search for.

**Response**: 
A list SERPResult objects. Each object contains the following fields:
  - ``score``: The ranked relevance score of the document.
  - ``url``: The URL of the document.
  - ``title``: The title of the document.
  - ``text``: The text of the document.
  - ``metadata``: A stringified JSON object containing the document's metadata.
  - ``dataset``: The name of the dataset the document belongs to.

**Example**:

.. code-block:: bash

   curl -X POST https://api.sciphi.ai/search \
        -H "Authorization: Bearer $SCIPHI_API_KEY" \
        -H "Content-Type: application/json" \
        -d '{"query": "What is quantum field theory in curved spacetime?"}'

**Response**:

.. code-block:: none

   [
    {
        "score": 0.9219069895529107,
        "url": "https://en.wikipedia.org/wiki/Quantum%20field%20theory%20in%20curved%20spacetime",
        "title": "Quantum field theory in curved spacetime",
        "dataset": "wikipedia",
        "text": "These theories rely on general relativity to describe a curved background spacetime, and define a generalized quantum field theory to describe the behavior of quantum matter within that spacetime."
    },
    {
        "score": 0.8924581032960278,
        "url": "https://arxiv.org/abs/1308.6773",
        "title": "Quantum field theory on curved spacetime and the standard cosmological model",
        "dataset": "arxiv",
        "text": "Algebraic quantum field theory was originally developed to understand the relation between the local degrees of freedom of quantized fields and the observed multi-particle states. It was then observed by Dimock and Kay that it provides a good starting point for formulating a theory on a curved spacetime."
    },
    ...
   ]

API Key and Signup
------------------

To access the AgentSearch API, you need an API key. If you don't possess one, you can sign up `here <https://www.sciphi.ai/signup>`_. Ensure you include the API key in your request headers as shown in the examples.
