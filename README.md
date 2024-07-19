# Recommendation-Bot Backend

This repoository is part of the whole Recommendation Bot project. This repository containes backend-end part of the RAG chatbot which can provide recommendation based on user queries and chat responses. It generates tag specific to user requirements and map those Tags to provided keys, which are later used to recommend products.



you can see implementation of the recommendadtion bot front-end [here](https://github.com/harsh201045/Recommendation-Bot-frontend)

[![Image of the front-end](https://github.com/user-attachments/assets/cdd2e1ec-795a-4df4-889b-baeb1dcfdc95)](https://github.com/Korat-Dishant/Recommendation-Bot)


## Run this project

Clone the project

```bash
  git clone https://github.com/harsh201045/Recommendation-Bot-Backend
```

Go to the project directory

```bash
  cd Recommendation-Bot-Backend
```

Install dependencies

```bash
    pip install requirements.txt
```

create `.env` file based on provided envTemplate

Start server 

```bash
  uvicorn API:app --reload
```

#### for swagger documantation
goto `http://localhost:8000/docs`

<img width="805" alt="swagger" src="https://github.com/user-attachments/assets/e1eb196f-842e-4d2e-b2c9-eaf0c7265c01">



## Architecture

![architecture](https://github.com/user-attachments/assets/66a1a5bc-46a8-4d4b-8f96-728cc1518a1a)


Recommendation Bot uses ...
- LLM to generate Recommendation tags and final response.
- When user queries the chatbot, based on previous chat history and current query it generate recommendation Tags 
- This tags are later used for key mapping dictionary to generate final tags. This Tag dictionary allows more control over generated Tags and makes the product searching more efficient. (ie if a LLM generates tag `summer`, Tag dictionary extends these tags like `summer clothing`, `light cloths`, `shorts`, `cotton`, `relax fit`, `tank tops` etc.)  
- These Generated Tags are later used for similarity search and most similar products are returned by milvus.
- Details of these products and user query and earlier chat context is again provided to LLM to generate final human like response. Which is later accessed by frontend and displayed to user.
  
