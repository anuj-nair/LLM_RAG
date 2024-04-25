# LLM_RAG
LLM Model + RAG using custom data 

Inspired By [RAG using Llama 2, Langchain and ChromaDB](https://www.kaggle.com/code/gpreda/rag-using-llama-2-langchain-and-chromadb)


## Installation
1. Create Python Environment
2. Install Required Python Libraries
   ```python
   pip install torch==2.0.1 chromadb==0.4.12 langchain==0.1.16 langchain-chroma==0.1.0 langchain-community==0.0.34 huggingface-hub==0.22.2 sentence-transformers==2.2.2 pypdf==4.2.0
   ```
   To Install Llama-CPP-Python  
   For this further information check this [link](https://python.langchain.com/docs/integrations/llms/llamacpp/)
   - CPU
     ```bash
     pip install llama-cpp-python
     ```
   - Mac Metal
     ```bash
     CMAKE_ARGS="-DLLAMA_METAL=on" FORCE_CMAKE=1 pip install llama-cpp-python
     ```
   - Nvidia GPU
     - Linux
       ```bash
       CMAKE_ARGS="-DLLAMA_CUBLAS=ON" FORCE_CMAKE=1 pip install llama-cpp-python
       ```
     - Windows check out this [link](https://medium.com/@piyushbatra1999/installing-llama-cpp-python-with-nvidia-gpu-acceleration-on-windows-a-short-guide-0dfac475002d)
       ```cmd
       set CMAKE_ARGS=-DLLAMA_CUBLAS=on
       set FORCE_CMAKE=1
       pip install llama-cpp-python
       ```
    
## Download LLM Model
Using HuggingFace CLI
```
huggingface-cli download TheBloke/Llama-2-7b-Chat-GGUF --local-dir model_files --local-dir-use-symlinks False --include='*Q4_K_M.gguf'
```
This will download Llama 3 8B Instruct LLM in `model_files` folder.

## Store Custom Data
Store your custom data in `docs` folder.  
Currently `txt`, `csv` and `pdf` file formats are supported.

## Run LLM_RAG.ipynb
1. It will load necessary python libraries 
2. Load the Llama 2 7B LLM
3. Load the All MiniLM L6 V2 embedding model
4. Load custom documents 
5. Convert custom documents to vectors using embedding model and store it to Chroma vector database.
6. LLM generates output to the question by retrieving relevant information from vector database. 