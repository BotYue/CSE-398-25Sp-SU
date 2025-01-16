
```shell
cao@raspberrypiCao:~ $ curl -fsSL https://ollama.com/install.sh | sh
>>> Installing ollama to /usr/local
>>> Downloading Linux arm64 bundle
######################################################################## 100.0%
>>> Creating ollama user...
>>> Adding ollama user to render group...
>>> Adding ollama user to video group...
>>> Adding current user to ollama group...
>>> Creating ollama systemd service...
>>> Enabling and starting ollama service...
Created symlink /etc/systemd/system/default.target.wants/ollama.service → /etc/systemd/system/ollama.service.
>>> The Ollama API is now available at 127.0.0.1:11434.
>>> Install complete. Run "ollama" from the command line.
WARNING: No NVIDIA/AMD GPU detected. Ollama will run in CPU-only mode.
cao@raspberrypiCao:~ $ ollama run llama3.2
pulling manifest 
pulling dde5aa3fc5ff... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 2.0 GB                         
pulling 966de95ca8a6... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 1.4 KB                         
pulling fcc5a6bec9da... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 7.7 KB                         
pulling a70ff7e570d9... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏ 6.0 KB                         
pulling 56bb8bd477a5... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏   96 B                         
pulling 34bb5ab01051... 100% ▕██████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████▏  561 B                         
verifying sha256 digest 
writing manifest 
success 
>>> you know syracuse?
Syracuse! Yes, I'm familiar with it. Syracuse is a city located in the state of New York, USA. It's known for being home to:

1. Syracuse University (SU), one of the largest and most prestigious private research universities in the country.
2. The Orange (University Athletics), whose teams compete in the Atlantic Coast Conference (ACC) and have won numerous NCAA championships.
3. The Syracuse Salt City, also known as the "Salt City" due to its history with salt production.

What would you like to know about Syracuse?

>>> 
Use Ctrl + d or /bye to exit.


```