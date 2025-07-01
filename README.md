# build-chatbot-for-your-data

pip3 install virtualenv 
virtualenv my_env # create a virtual environment my_env
source my_env/bin/activate # activate my_env


git clone https://github.com/ibm-developer-skills-network/wbphl-build_own_chatbot_without_open_ai.git
mv wbphl-build_own_chatbot_without_open_ai build_chatbot_for_your_data
cd build_chatbot_for_your_data

pip install -r requirements.txt

pip install langchain-community


(optional) Using HuggingFace API for the worker

pip install langchain==0.1.17
pip install huggingface-hub==0.23.4

* The `HuggingFace` is hosting some LLM models which can be called free (if the model is below 10GB). You can also download any model and run it locally.

``` 
def init_llm():
    global llm_hub, embeddings
    # Set up the environment variable for HuggingFace and initialize the desired model.
    os.environ["HUGGINGFACEHUB_API_TOKEN"] = "Your HuggingFace API"

    # Insert the name of repo model
    model_id = "mistralai/Mistral-7B-Instruct-v0.3"
    
    # load the model into the HuggingFaceHub
    llm_hub = # --> specify hugging face hub object with (repo_id, model_kwargs={"temperature": 0.1, "max_new_tokens": 600, "max_length": 600})
    
    #Initialize embeddings using a pre-trained model to represent the text data.
    embeddings = # --> create object of Hugging Face Instruct Embeddings with (model_name,  model_kwargs={"device": DEVICE} )
    ```