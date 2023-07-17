# Vicuna-13b-GPTQ-4bit-128g

Vicuna-13B is an open-source chatbot trained on user-shared conversations from ShareGPT using LLaMA. Preliminary evaluation with GPT-4 as a judge validates its performance.

NOTE: It may take some time for the Installation on first time! ⚠️

Join [Discord](https://discord.gg/P9gGZaXWGR) for any Assist/Issues 

## Key Features
- State-of-the-art model resources (weights, training code, and evaluation code) like Vicuna and FastChat-T5.
- Distributed multi-model serving system with web UI and OpenAI-compatible RESTful APIs.


## First Method!
1. Access Google Colab: Visit <a href="https://colab.research.google.com/drive/1oKPWrtW98Oxz2iLc194HhqOJHk8p4Onv?usp=sharing" target="_blank">Google Colab</a> to get started with Vicuna-13b-GPTQ-4bit-128g.
2. To Ensure Proper Execution, run each Colab cell starting from the beginning.
4. To host a public Gradio URL, you can use the last cell and visit the provided Gradio hosted link.


## Second Method!
1. Access Google Colab: Visit [Google Colab](https://colab.research.google.com/).
2. Create a new Colab notebook.
3. Copy this Code Given Below and Execute the Cell!

```python
%cd /content
!apt-get -y install -qq aria2
```

4. After executing the first cell, make another cell and run the following code:
   
```python
!git clone -b v1.7 https://github.com/camenduru/text-generation-webui
%cd /content/text-generation-webui
!pip install -r requirements.txt
!pip install -U gradio==3.28.3
```

5. After executing the Second cell, make another cell and run the following code:

```python
!mkdir /content/text-generation-webui/repositories
%cd /content/text-generation-webui/repositories
!git clone -b v1.2 https://github.com/camenduru/GPTQ-for-LLaMa.git
%cd GPTQ-for-LLaMa
!python setup_cuda.py install
```


6. After executing the Third cell, make another cell and run the following code:

```python
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/raw/main/config.json -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o config.json
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/raw/main/generation_config.json -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o generation_config.json
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/raw/main/special_tokens_map.json -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o special_tokens_map.json
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/resolve/main/tokenizer.model -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o tokenizer.model
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/raw/main/tokenizer_config.json -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o tokenizer_config.json
!aria2c --console-log-level=error -c -x 16 -s 16 -k 1M https://huggingface.co/4bit/vicuna-13b-GPTQ-4bit-128g/resolve/main/vicuna-13b-4bit-128g.safetensors -d /content/text-generation-webui/models/vicuna-13b-GPTQ-4bit-128g -o vicuna-13b-4bit-128g.safetensors
```

7. After executing the Fourth cell, make another cell and run the following code to Host a Gradio WebUI:

```python
%cd /content/text-generation-webui
!python server.py --share --chat --wbits 4 --groupsize 128
```

Enjoy the WebUI and have a look at [Vicuna-13b-GPTQ-4bit-128g](https://github.com/lm-sys/FastChat) for Training and Local Installation!

