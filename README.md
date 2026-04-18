[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/UglRn7sb)

Gen AI Project
--
Part 2: Create a Retrieval-Augmented Generation (RAG) application with 2 helper functions and compare its performance with vanilla RAG and LLM for 5 different prompts. 

Python Requirements
--
This project requires Python 3.8 or later. Libraries needed are listed in the `requirements.txt` file.

How to Run
--
1. Create a `.env` file to store API keys:
- Include the Pinecone API key (for storing and retrieving vectors)
- Include the OpenAI API key (for using ChatGPT LLM)
2. Edit `rag.ipynb`:
- Open `rag.ipynb` and update the file path inside `load_dotenv()` to correctly locate the `.env` file with API keys.
3. Set up the environment:
- Install dependencies using `requirements.txt`.
- Run `rag.ipynb` cells in order.

Files Included
--
- `rag.ipynb`: Jupyter Notebook with HW 1 - Part 2 implementation in the project description above and comments on model performances for different prompts.
- `requirements.txt`: Python dependencies.
- `sample_output.pdf`: Sample output showing LLM, RAG, and advanced RAG outputs for different prompts.
