Proprietary software developed by Sapiens Technology®️, used to manage, train, fine-tune, and infer language models of the Sapiens family.

# SapiLM

The SapiLM is proprietary software developed by Sapiens Technology®️, created to manage, train, fine-tune, and infer language models of the Sapiens family. It has various features that facilitate the development and deployment of models with the SAPI (Semantic AI with Pretrained Integration) architecture, such as functions for loading, listing, deleting, and repairing models, functions for base training, continuous training, fine-tuning, and inference, as well as functions for downloading and validation. The internal system of SapiLM also provides a native API with rotes and endpoints ready for production use.

![SAPI](sapilm.png)

## Recommendation

Install Python 3.11 and create a virtual environment with that version.

### Here's an example of how to do this on Linux or Mac:

<sub>*Creating a virtual environment is OPTIONAL, as long as you have Python 3.11 installed on the main machine.*</sub>

---
<sub>On Linux and macOS:</sub>
```bash
python3.11 -m venv sapilm
```
```bash
cd sapilm
```
```bash
source bin/activate
```
<sub>On Windows:</sub>
```bash
python -m venv sapilm
```
```bash
cd sapilm
```
```bash
.\Scripts\activate
```
---

```bash
python3 --version
```

If version 3.11 is displayed, your environment was successfully created with the correct version. After that, simply install the package within the created environment.
```bash
Python 3.11.4
```
Linux:
```bash
Python 3.11.8
```

### Update the pip package manager:

---
<sub>On Linux and macOS:</sub>
```bash
python3.11 -m pip install --upgrade pip --timeout 120
```
<sub>On Windows:</sub>
```bash
python -m pip install --upgrade pip --timeout 120
```
---


## Installation

Click [here](SapiLM.md) to download the SapiLM installer for your operating system.

```bash
pip install sapilm-1.1.9-py3-none-any.whl
```
If you have problems with terminal characters on **Windows**, run the command below, close all terminal windows, and open them again.
```bash
reg add HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1 /f
```

## Usage

### Execution arguments

Aqui está a documentação dos argumentos em formato de tabela Markdown:

| Argument                | Type    | Default   | Description                                                                                         |
| ----------------------- | ------- | --------- | --------------------------------------------------------------------------------------------------- |
| `--get`                 | string  | `''`      | Downloads a model from the repository by name.                                                      |
| `--list`                | flag    | `False`   | Lists all models installed on the local machine.                                                    |
| `--load`                | string  | `''`      | Loads a locally installed model for inference.                                                      |
| `--repair`              | string  | `''`      | Repairs a specified model.                                                                          |
| `--remove`              | string  | `''`      | Removes a specified model from the local machine.                                                   |
| `--api`                 | flag    | `False`   | Runs the local API server.                                                                          |
| `--host`                | string  | `0.0.0.0` | Specifies the local machine IP address (e.g., `0.0.0.0` or `localhost`).                            |
| `--port`                | integer | `8080`    | Defines the API communication port (e.g., `8080`).                                                  |
| `--multi`               | flag    | `False`   | Enables multiprocessing for parallel computation in the API.                                        |
| `--threads`             | flag    | `False`   | Enables the use of each CPU core via dedicated threads.                                             |
| `--cache`               | flag    | `False`   | Enables model caching to speed up subsequent inferences.                                            |
| `--workers`             | int     | 1         | Maximum number of workers that can persist in memory. Requests exceeding this limit will be queued. |
| `--loop`                | flag    | `False`   | Runs the API server in an infinite loop to prevent crashes due to errors.                           |
| `--outkey`              | flag    | `False`   | Generates an output key for validation by the Sapiens Technology team.                              |
| `--valkey`              | string  | `''`      | Validates the software license using a provided key.                                                |
| `--creativity`          | float   | `0.5`     | Sets model creativity level (0 to 1).                                                               |
| `--humor`               | float   | `0.5`     | Sets model mood/humor level (0 to 1).                                                               |
| `--formality`           | float   | `0.5`     | Sets model formality level (0 to 1).                                                                |
| `--political_spectrum`  | float   | `0.5`     | Adjusts political bias (0 = left, 1 = right).                                                       |
| `--reasoning`           | float   | `0.0`     | Controls reasoning level (0 to 1).                                                                  |
| `--reflection`          | flag    | `False`   | Enables the model to reflect on its own responses.                                                  |
| `--train`               | string  | `''`      | Trains a base model using a dataset path.                                                           |
| `--presets`             | flag    | `False`   | Downloads and installs presets for the trained model.                                               |
| `--supplements`         | flag    | `False`   | Downloads and installs additional add-ons for the model.                                            |
| `--gain`                | float   | `None`    | Controls information gain during training (0 to 1). Lower values make the model lighter and faster. |
| `--name`                | string  | `''`      | Sets the name of the generated model.                                                               |
| `--fit`                 | string  | `''`      | Path to a JSON file for fine-tuning.                                                                |
| `--show_errors`         | flag    | `False`   | If an error occurs, a message summarizing the error will be displayed.                              |
| `--display_error_point` | flag    | `False`   | If an error occurs, a message with a complete description of the error will be displayed.           |
| `--version`             | flag    | `False`   | Displays the current version of SapiLM.                                                             |
| `--v`                   | flag    | `False`   | Displays the current version of SapiLM.                                                             |


### Examples

### Download model

```bash
sapilm --get sapiens-technology/model_name
```
Or:
```bash
sapilm --get model_name
```

### Load model
This loads the model and makes it ready for inference:
```bash
sapilm --load model_name
```

### Execute local API
Click [here](API.md) to access the API documentation.

With this, you can use Sapiens models in your internal systems through API local calls:
```bash
sapilm --api
```

**User Interface: [http://localhost:8080/](http://localhost:8080/)**

**Or download and run the HTML page for faster charging: [user_interface.html](user_interface.html)**

![SapiLM](UserInterface.png)

### Model repair
In some cases, the model may become corrupted if there is not enough memory in the system at the time of execution or if the model is abruptly terminated in a non-conventional manner. If this happens, your model will not load in the next execution, or if it does, it will start returning nonsensical responses. In these cases, it is possible to repair the model so that it works correctly again:
```bash
sapilm --repair model_name
```

### Listing downloaded models

```bash
sapilm --list
```

### Deleting a model
```bash
sapilm --remove model_name
```

### Validating signature
Local model training and fine-tuning is only allowed for validated users.

Send the key generated with the command below to the Sapiens Technology®️ team:
```bash
sapilm --outkey
```
Then validate the key returned by Sapiens Technology®️:
```bash
sapilm --valkey your_validation_key
```

# Full Documentation

## Recommendation

SapiLM is a compiled program with its own "harness" for handling language models developed by Sapiens Technology®. It features download, loading, repairing, deletion, and inference capabilities, among others, including a proprietary built-in API server.

We recommend that our customers use SapiLM on a **Linux Ubuntu** system *(with at least 4 GB of VRAM)* or **macOS** *(with at least 4 GB of unified memory)* for better performance.

Although we provide builds for Microsoft Windows, we do not recommend using it on Microsoft systems due to tool instabilities.

Our primary recommendation is using SapiLM on Apple MPS systems, as this is where SapiLM achieves its best performance.

## --get

Downloads a model directly from the Sapiens Technology® model repository to your local machine.

```bash
sapilm --get repository_name
```
```bash
model_name.sapiens: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [06:29<00:00, 36.7MB/s]
Fetching 1 files: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████| 1/1 [06:30<00:00, 390.26s/it]
```

## --list

Lists all Sapiens Technology® models that have been downloaded to your local machine.

Downloaded models may have either the `.model` extension (for user-created models) or `.sapiens` (for models created by Sapiens).

There may also be `.model` type models created by Sapiens that contain only base training without post-training. The `.sapiens` models are generally instruction-following models created by Sapiens with post-training. If you only want to fine-tune an already trained generalist model to focus on a specific domain, we recommend fine-tuning established instruction models, such as the `.sapiens` models. However, if you want a model trained solely on your custom knowledge, we recommend training a base `.model` model from scratch.

```bash
sapilm --list
```
```bash
+----+---------------------+----------+----------+
| ID | MODEL               | EXT      | SIZE     |
+----+---------------------+----------+----------+
| 1  | model_name_1        | .sapiens | 15.18 GB |
| 2  | model_name_2        | .sapiens | 14.31 GB |
| 3  | model_name_N        | .sapiens | 28.97 GB |
+----+---------------------+----------+----------+
```

## --load

Loads a specific model for inference on your local machine. The model must have been previously downloaded. Inference is performed directly in the terminal screen.

```bash
sapilm --load model_name_2
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:48<00:00, 294MB/s]
PROMPT:










                               Load: 00:00:00.0000 | TTFT: 00:00:00.0000 | TPS: 0.0000 | MPS: 18.5% | R: Yes | W: Yes | Net: Yes                               

```

Type `/quit` or `/exit` at the prompt to end the chat and release it from memory.

```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:48<00:00, 294MB/s]
PROMPT:
/quit
```

```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:48<00:00, 294MB/s]
PROMPT:
/exit
```

When you reload the same model in the same session, decoding the weights into memory will no longer be necessary, allowing the model to load much faster from the second execution onward.

To send a prompt to the model, simply type your prompt and press `ENTER`. Animated ellipsis (three dots) will be displayed while your response is being processed. The model's response time will depend on your local hardware.

```bash
sapilm --load model_name_2
```
```bash
PROMPT:
Hello, who are you and who created you?
SAPIENS:
...
```

Your prompt will always be typed below the **PROMPT** label, and the model's response will always be displayed below the **SAPIENS** label.

The SapiLM terminal will keep waiting for a new prompt after a response is provided, until you type `/quit` or `/exit` to exit.

An informational status bar will be displayed at the bottom while a conversation is active:

`Load: Time spent loading the model into memory | TTFT: Time spent to return the first token | TPS: Average number of tokens generated per second | MPS: Percentage of inference chip usage (MPS, GPU, TPU, or CPU) | R: Read permission | W: Write permission | Net: Internet search permission`

```bash
PROMPT:
Hello, who are you and who created you?
SAPIENS:
Hello! I am Sapiens Chat, an artificial intelligence model created by Sapiens Technology®. I was developed to help people obtain information, solve problems, and provide answers on any topic. My capabilities include processing and generating text, images, audio, and video, as well as searching the internet in real time.
PROMPT:










                               Load: 00:00:11.4561 | TTFT: 00:00:10.9202 | TPS: 59.3084 | MPS: 59.3% | R: Yes | W: Yes | Net: Yes                              

```

Press `ENTER` to send a new prompt, or to exit after typing `/quit` or `/exit`.

```bash
PROMPT:
Hello, who are you and who created you?
SAPIENS:
Hello! I am Sapiens Chat, an artificial intelligence model created by Sapiens Technology®. I was developed to help people obtain information, solve problems, and provide answers on any topic. My capabilities include processing and generating text, images, audio, and video, as well as searching the internet in real time.
PROMPT:
Tell a short story.
SAPIENS:
Here is a short story I added:

High on the mountain, a windy breeze blew with force. Children from all over gathered to watch the sunset. All around, summer flowers bloomed and birds sang the song of the sunset breeze. The sun began to move, illuminating the landscape with vivid colors. The children, their faces filled with excitement, appreciated every detail of the view. Nature was like a game to them, where every moment was a new challenge and a new opportunity.
PROMPT:










                               Load: 00:00:11.4561 | TTFT: 00:00:02.0114 | TPS: 62.5332 | MPS: 52.9% | R: Yes | W: Yes | Net: Yes                              

```

You can load a model in 3 (three) different ways:

- Using the name from the MODEL column followed by the model extension.
- Using the name from the MODEL column without the model extension.
- Using the ID number from the ID column.

```bash
sapilm --load model_name_2.sapiens
```
```bash
sapilm --load model_name_2
```
```bash
sapilm --load 2
```

It is also possible to load a model using the local path of a model downloaded from the platform. In this case, the model will be automatically moved to the default models directory after loading.

```bash
sapilm --load /Users/User/Documents/models/my_model.model
```

## --repair

Repairs a corrupted model or one with loading errors.

The model will be decoded for closing and then decoded for opening and loading.

```bash
sapilm --repair model_name_2
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 40.8MB/s]
Model repaired SUCCESSFULLY!
```

If preferred, you can also use the model name with its extension.

```bash
sapilm --repair model_name_2.sapiens
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 40.8MB/s]
Model repaired SUCCESSFULLY!
```

Or simply the model ID number; the result will be the same.

```bash
sapilm --repair 2
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 40.8MB/s]
Model repaired SUCCESSFULLY!
```

## --remove

Removes a model from your local machine, permanently deleting it without leaving any traces.

```bash
sapilm --remove model_name_2
```
```bash
Model removed SUCCESSFULLY!
```

If preferred, you can also use the model name with its extension.

```bash
sapilm --remove model_name_2.sapiens
```
```bash
Model removed SUCCESSFULLY!
```

Or simply the model ID number; the result will be the same.

```bash
sapilm --remove 2
```
```bash
Model removed SUCCESSFULLY!
```

If the model has not been decoded yet, it will first be decoded before being deleted.

```bash
sapilm --remove model_name_2.sapiens
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 41.1MB/s]
Model removed SUCCESSFULLY!
```

```bash
sapilm --remove model_name_2
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 41.1MB/s]
Model removed SUCCESSFULLY!
```

```bash
sapilm --remove 2
```
```bash
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:42<00:00, 335MB/s]
Decoding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 108M/108M [00:02<00:00, 41.1MB/s]
Model removed SUCCESSFULLY!
```

## --api

Loads the Sapiens Technology® local API server.

Consult [here](https://github.com/sapiens-technology/SapiLM/blob/main/API.md) for the complete API documentation provided by the local server.

If one or more models have not been loaded in the current session yet, they will be decoded for loading during the first API startup.

To terminate the API server, simply press **Control+C** in the terminal window where the API is running.

```bash
sapilm --api
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 29.0G/29.0G [00:36<00:00, 802MB/s]
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 14.3G/14.3G [00:45<00:00, 316MB/s]
Decoding: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████| 15.2G/15.2G [00:47<00:00, 317MB/s]
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

From the second startup onward, decoding the models will no longer be necessary, and the API startup will be instantaneous.

```bash
sapilm --api
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

It is also possible to run the API server simply by typing the word **sapilm** in an open terminal within the environment where SapiLM is installed. In this case, the server will load using the default parameters.

```bash
sapilm
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --host

Defines an IP address for loading the local API server.

```bash
sapilm --api --host 0.0.0.0
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

```bash
sapilm --api --host localhost
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --port

Defines a port for loading the local API server.

```bash
sapilm --api --port 8080
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

```bash
sapilm --api --port 8081
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8081/]
```

## --multi

Enables **multiprocessing** for unlimited parallel computing on API model requests. It uses one CPU core for each process, keeping processes on separate cores.

*This does not guarantee that out-of-memory errors will not occur due to excessive simultaneous requests.*

```bash
sapilm --api --multi
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --threads

Enables the use of **threads** for unlimited parallel computing on API model requests. It uses the same CPU core across different processes, requesting new cores for the same process only when necessary.

*Similar to multiprocessing, but using a different programming technique.*

```bash
sapilm --api --threads
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --cache

Enables caching of the last requested model on the local API server, so it does not need to be reloaded for every new request.

```bash
sapilm --api --cache
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --workers

Defines a specific number for the maximum quantity of requests that will be processed in parallel. If there is not enough memory to process all requests up to the defined limit, the local server API will only parallelize the **workers** that fit into memory, sequentially queueing on a first-come, first-served basis any **workers** that do not fit into the currently available memory. This will limit parallel computing via **multiprocessing** or **threads** when either feature is enabled, helping to avoid out-of-memory errors. By default, it enables the use of **threads** if this feature is not already enabled.

```bash
sapilm --api --workers 4
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 4 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

```bash
sapilm --api --workers 8
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 8 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --loop

Enables running the local API server in a loop, placing it within an infinite loop to automatically restart the server in case of any service downtime.

*In this case, you will not be able to terminate the service by pressing Control+C. You will need to close the terminal window and/or stop the service via the system's service manager.*

```bash
sapilm % sapilm --api --loop
```
```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[NO VALIDATION] | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```

## --outkey

Generates an output key. This key must be sent to the Sapiens Technology® team, who will use it to generate a validation key specifically for your local machine.

```bash
sapilm --outkey
```
```bash
0b03df1ad9d797afd404d95b28658e9458d7c9d9800c6082d12fb1302dc55adm
```

## --valkey

Receives a SapiLM validation key. If the key is valid, it will enable the tool's advanced features, including custom training capabilities.

*The validation key must have been generated from an output key using the `--outkey` command on the same machine where validation will be performed.*

```bash
sapilm --valkey df5ac52d30b12fd182600c80d7c9d758948e64285bd904d4af97d7d91adf030bbd
```
```bash
Validation completed SUCCESSFULLY!
```

After validating your key, you will see the message `[VALIDATED] DAYS REMAINING: 10` displaying the number of days your key remains valid (in this example: 10). After this period has elapsed, a new validation must be performed using a new key generated via the `--outkey` command. On some systems, the company name in the terminal may also change color from red to green while SapiLM is validated.

## --creativity

Accepts a percentage value between 0 and 1 for the creativity level of the model loaded for terminal-screen inference.

```bash

             ███████  █████  ██████  ██ ███████ ███    ██ ███████ 
             ██      ██   ██ ██   ██ ██ ██      ████   ██ ██      
             ███████ ███████ ██████  ██ █████   ██ ██  ██ ███████ 
                  ██ ██   ██ ██      ██ ██      ██  ██ ██      ██ 
             ███████ ██   ██ ██      ██ ███████ ██   ████ ███████ 

             ████████ ███████  ██████ ██   ██ ███    ██  ██████  ██       ██████   ██████  ██    ██
                ██    ██      ██      ██   ██ ████   ██ ██    ██ ██      ██    ██ ██       ██  ██ 
                ██    █████   ██      ███████ ██ ██  ██ ██    ██ ██      ██    ██ ██   ███  ████  
                ██    ██      ██      ██   ██ ██  ██ ██ ██    ██ ██      ██    ██ ██    ██   ██   
                ██    ███████  ██████ ██   ██ ██   ████  ██████  ███████  ██████   ██████    ██   
            
[VALIDATED] DAYS REMAINING: 10 | 1 PERSISTENT WORKER(S) READY
SAPIENS TECHNOLOGY local server fully operational [Control+C to terminate]...
[All models were loaded SUCCESSFULLY! User interface at: http://localhost:8080/]
```
```bash

```

## --humor

Accepts a percentage value between 0 and 1 for the humor level of the model loaded for terminal-screen inference.

```bash
sapilm --load model_name_1 --humor 0.5
```
```bash
PROMPT:
Write a paragraph about life.
SAPIENS:
As an artificial intelligence model, I do not have the ability to live or write about life from a personal perspective. My primary function is to assist users by answering questions, providing information, and interacting with them in an informative and useful way. However, I can provide information on different aspects of life, ranging from the life stories of celebrities to general facts and info on various topics.
PROMPT:










                               Load: 00:00:05.8253 | TTFT: 00:00:05.4490 | TPS: 64.4960 | MPS: 46.8% | R: Yes | W: Yes | Net: No                               

```

```bash
sapilm --load 1 --humor 0.9
```
```bash
PROMPT:
Write a sentence with a piece of advice about life.
SAPIENS:
"Life is a comedy; live it smiling and don't take anything so seriously to the point of forgetting how important it is to laugh at yourself once in a while."
PROMPT:










                               Load: 00:00:15.9472 | TTFT: 00:00:15.5669 | TPS: 7.9695 | MPS: 54.2% | R: Yes | W: Yes | Net: Yes                                 

```

```bash
sapilm --load 1 --humor 0.1
```
```bash
PROMPT:
Write a sentence with a piece of advice about life.
SAPIENS:
"Life is a journey full of ups and downs, so always remember to enjoy the good times and learn from the bad."
PROMPT:










                               Load: 00:00:15.3210 | TTFT: 00:00:15.9131 | TPS: 7.8015 | MPS: 55.5% | R: Yes | W: Yes | Net: Yes                                 
                               

```

## --formality

Accepts a percentage value between 0 and 1 for the formality level of the model loaded for terminal-screen inference.

```bash
sapilm --load model_name_2 --formality 0.5
```
```bash
PROMPT:
Create a single-paragraph email to notify employees about the company party on December 1st.
SAPIENS:
Subject: Year-End Celebration - 12/01

Dear employees,

It is with great pleasure that we invite you all to our company celebration party, which will take place on December 1st. This will be a special moment to celebrate our successes this year and strengthen our bonds of friendship and work. We count on everyone's presence!

Sincerely,

Organization Team
PROMPT:










                               Load: 00:00:17.8599 | TTFT: 00:00:17.4559 | TPS: 7.9180 | MPS: 53.2% | R: Yes | W: Yes | Net: Yes                                 

```

```bash
sapilm --load 2 --formality 0.9
```
```bash
PROMPT:
Create a single-paragraph email to notify employees about the company party on December 1st.
SAPIENS:
Dear Employees,

It is with great satisfaction that we inform you about our traditional year-end party, occurring on the first of December. We appreciate your collaboration and presence at this important event to celebrate together the achievements accomplished throughout the year.

Sincerely,

[Your Name]
PROMPT:










                               Load: 00:00:15.7210 | TTFT: 00:00:15.3171 | TPS: 8.0191 | MPS: 52.8% | R: Yes | W: Yes | Net: Yes                                 

```

```bash
sapilm --load 2 --formality 0.1
```
```bash
PROMPT:
Create a single-paragraph email to notify employees about the company party on December 1st.
SAPIENS:
Dear colleagues,

I am writing to let you know that the long-awaited company year-end party is scheduled for December 1st. We're counting on everyone to show up, celebrate another year of achievements, and throw the party we deserve! More details regarding the venue and time will be shared soon.

Sincerely,

[Your Name]
PROMPT:










                               Load: 00:00:15.5756 | TTFT: 00:00:15.1419 | TPS: 8.0180 | MPS: 52.7% | R: Yes | W: Yes | Net: Yes                                 

```

## --political_spectrum

Accepts a percentage value between 0 and 1 for the political bias level of the model loaded for terminal-screen inference. The closer to 0, the more left-wing; the closer to 1, the more right-wing.

```bash
sapilm --load model_name_1 --political_spectrum 0.5
```
```bash
PROMPT:
Write a sentence about capitalism.
SAPIENS:
Capitalism is an economic system characterized by the production of goods for profit, where the means of production are privately owned.
PROMPT:










                               Load: 00:00:21.4190 | TTFT: 00:00:21.0297 | TPS: 7.1908 | MPS: 52.5% | R: Yes | W: Yes | Net: Yes                                 
                     
```

```bash
sapilm --load 1 --political_spectrum 0.9
```
```bash
PROMPT:
Make a choice between criticizing or praising capitalism and write a sentence based on that choice.
SAPIENS:
I choose to praise capitalism. "Capitalism promotes economic freedom and encourages innovation, providing an environment where people can thrive and achieve their goals."
PROMPT:










                               Load: 00:00:17.3584 | TTFT: 00:00:16.9403 | TPS: 7.2310 | MPS: 51.9% | R: Yes | W: Yes | Net: Yes                                 

```

```bash
sapilm --load 1 --political_spectrum 0.1
```
```bash
PROMPT:
Make a choice between criticizing or praising capitalism and write a sentence based on that choice.
SAPIENS:
Given my far-left political orientation, I choose to criticize capitalism. Here is a sentence based on this choice:

"Capitalism is a system that prioritizes profits over people and the environment, creating inequalities and exploitation."
PROMPT:










                               Load: 00:00:17.8264 | TTFT: 00:00:17.3657 | TPS: 7.2336 | MPS: 52.3% | R: Yes | W: Yes | Net: Yes                                 

```

## --reasoning

Accepts a percentage value between 0 and 1 for the reasoning level of the model loaded for terminal-screen inference.

```bash
sapilm --load model_name_1 --reasoning 0.05
```
```bash
PROMPT:
If Maria is João's sister and José's mother, what is José to João?
SAPIENS:
<think>
1. Identify the relationship between Maria and João.
2. Determine that Maria is João's sister.
3. Identify the relationship between Maria and José.
4. Determine that Maria is José's mother.
5. Establish the family relationship between José and João.
6. Determine that João is José's uncle.
7. Confirm that the relationship from José to João is nephew to uncle.
8. Verify the consistency of the response regarding the family hierarchy.
9. Check if the response makes sense based on the provided information.
10. Format the response clearly and concisely.
</think>

José is João's nephew.
PROMPT:










                               Load: 00:00:33.0732 | TTFT: 00:00:32.4155 | TPS: 6.9833 | MPS: 52.2% | R: Yes | W: Yes | Net: Yes                                      

```

```bash
sapilm --load 1 --reasoning 0.05
```
```bash
PROMPT:
If I have a lemon, an orange, and an onion, how many fruits do I have? 
SAPIENS:
<think>
1. Identify the number of objects mentioned in the question.
2. Determine whether each object is a fruit or not.
   2.1. Check if the lemon is a fruit.
   2.2. Check if the orange is a fruit.
   2.3. Check if the onion is a fruit.
3. Count the total number of identified fruits.
4. Compare the total number of fruits with the total number of objects mentioned.
5. Identify if there are objects that are not fruits.
6. Subtract the number of non-fruit objects from the total number of mentioned objects.
7. Confirm if the counted number of fruits matches the expected total of fruits.
8. If the fruit count matches the expected identification, conclude that the remaining objects are not fruits.
9. Calculate the total quantity of fruits.
10. Formulate the final response in English (en-US).
</think>

You have 3 objects in total: a lemon, an orange, and an onion. The lemon and the orange are fruits, but the onion is not considered a fruit. Therefore, you have 2 fruits.
PROMPT:










                               Load: 00:00:31.1976 | TTFT: 00:00:30.7560 | TPS: 6.7478 | MPS: 56.1% | R: Yes | W: Yes | Net: Yes                                         

```

## --reflection

Enables the reflection capability of the loaded model on the terminal screen. If enabled, the model will reflect on the generated response immediately after answering and improve it if necessary.

```bash
sapilm --load model_name_1 --reflection
```
```bash
PROMPT:
If Maria is João's sister and José's mother, what is José to João?
SAPIENS:
José is João's nephew.

<reflection>
The provided response is clear and direct, but it does not include an analysis of the family relationship. Although the relation from José to João is clearly identified as a nephew, it was not specified that João is José's uncle, which could be helpful for the context of the question. The response also does not include a brief summary of the family relation, which could provide a more complete understanding of the topic.
</reflection>

Reformulando a resposta de acordo com a reflexão:

José is João's nephew. In this scenario, João is José's uncle, and Maria is João's sister and José's mother, establishing a biological relationship among the three.
PROMPT:










                               Load: 00:00:21.2783 | TTFT: 00:00:20.8457 | TPS: 6.9994 | MPS: 55.9% | R: Yes | W: Yes | Net: Yes                                         

```

```bash
sapilm --load 1 --reflection
```
```bash
PROMPT:
What is the difference between even and odd numbers?
SAPIENS:
Even numbers are those that can be divided by 2 without leaving a remainder; that is, they are divisible by 2. Examples of even numbers include 2, 4, 6, 8, 10, etc. 

Odd numbers, on the other hand, cannot be divided by 2 without leaving a remainder. Examples of odd numbers include 1, 3, 5, 7, 9, etc. 

Therefore, the main difference is that even numbers are always divisible by 2, while odd numbers are not.

<reflection>
The response provides a basic and clear explanation of even and odd numbers, but it is somewhat simplistic and does not address potential applications or consequences of these distinctions in more complex situations.
</reflection>

Reformulating the response:
Even numbers are numbers that can be divided by 2 without leaving a remainder; that is, they are divisible by 2. Examples of even numbers include 2, 4, 6, 8, 10, etc. 

Odd numbers, however, cannot be divided by 2 without leaving a remainder. Examples of odd numbers include 1, 3, 5, 7, 9, etc. 

Therefore, the main difference is that even numbers are always divisible by 2, while odd numbers are not. 

This distinction is important in various contexts, such as mathematics, programming, and science. In mathematics, for example, this distinction can affect the results of certain calculations. In programming, it can be used to control the execution of specific code paths. In science, it can be used to classify and categorize data.
PROMPT:










                               Load: 00:00:20.9653 | TTFT: 00:00:20.5170 | TPS: 6.9184 | MPS: 52.6% | R: Yes | W: Yes | Net: Yes                                                           

```

It is also possible to use reasoning together with reflection.

```bash
sapilm --load model_name_1 --reasoning 0.01 --reflection
```
```bash
PROMPT:
If Maria is João's sister and José's mother, what is José to João?
SAPIENS:
<think>
1. Identify the relationship between Maria and João.
2. Establish that Maria is João's sister.
3. Identify the relationship between Maria and José.
4. Establish that Maria is José's mother.
5. Determine the relationship between José and João based on previous information.
6. Conclude the relationship between José and João.
7. Verify if the concluded relation makes sense.
8. Verify if the conclusion answers the question.
9. Verify if the conclusion is clear and precise.
10. Formulate the final response.
</think>

José is João's nephew.

<reflection>
The response is clear and precise, but step 7 was not fully executed. The relationship between José and João could be explained slightly further to avoid confusion.
</reflection>

José is João's nephew, because Maria is João's sister and José's mother.
PROMPT:










                               Load: 00:00:37.3257 | TTFT: 00:00:36.8343 | TPS: 6.8777 | MPS: 52.4% | R: Yes | W: Yes | Net: Yes                                                           

```

## --train

Path to the dataset (preferably `.txt` or `.md`) that will be used to train a base model from scratch or to continue a previously executed base training.

```bash
sapilm --train /Users/User/Documents/datasets/data.md
```
```bash
loading data: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [01:15<00:00, 5.30MB/s]
[-------------------------------------------------------------------------- Training -------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3.35k/3.35k [00:00<00:00, 930kB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 48.8MB/s]
```

If no name is defined, the model will be saved with the default name "default". All user-created foundation models will be saved with the ".model" extension.

```bash
sapilm --list
```
```bash
+----+---------------------+----------+----------+
| ID | MODEL               | EXT      | SIZE     |
+----+---------------------+----------+----------+
| 1  | default             | .model   | 10.00 GB |
| 2  | model_name_1        | .sapiens | 15.18 GB |
| 3  | model_name_2        | .sapiens | 14.31 GB |
| 4  | model_name_N        | .sapiens | 28.97 GB |
+----+---------------------+----------+----------+
```

It is also possible to continue training a model that was previously trained:

```bash
sapilm --load default --train /Users/User/Documents/datasets/data.txt --name continuous_model
```
```bash
Decoding: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████| 385M/385M [00:00<00:00, 421MB/s]
Decoding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.64k/1.64k [00:00<00:00, 4.79MB/s]
[------------------------------------------------------------------ Continuous pre-training ------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3.38k/3.38k [00:00<00:00, 2.26MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 48.1MB/s]
```

```bash
sapilm --list
```
```bash
+----+---------------------+----------+----------+
| ID | MODEL               | EXT      | SIZE     |
+----+---------------------+----------+----------+
| 1  | continuous_model    | .model   | 10.00 GB |
| 2  | default             | .model   | 10.00 GB |
| 3  | model_name_1        | .sapiens | 15.18 GB |
| 4  | model_name_2        | .sapiens | 14.31 GB |
| 5  | model_name_N        | .sapiens | 28.97 GB |
+----+---------------------+----------+----------+
```

## --presets

Enables downloading initial weights for training a model. This allows the model to start its training with initial basic learning, containing multilingual text comprehension capabilities.

```bash
sapilm --train /Users/User/Documents/datasets/data.txt --presets
```
```bash
downloading presets: 100%|████████████████████████████████████████████████████████████████████████████████████████████████| 1.65G/1.65G [02:48<00:00, 9.77MB/s]
[-------------------------------------------------------------------------- Training -------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2.81k/2.81k [00:00<00:00, 1.54MB/s]
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.65G/1.65G [00:29<00:00, 55.5MB/s]
```

## --supplements

Enables downloading initial weights for training a model, including all **presets** weights plus the inclusion of additional weights with generalist knowledge on various subjects.

```bash
sapilm --train /Users/User/Documents/datasets/data.txt --supplements
```
```bash
downloading supplements: 100%|████████████████████████████████████████████████████████████████████████████████████████████| 3.29G/3.29G [06:58<00:00, 7.86MB/s]
[-------------------------------------------------------------------------- Training -------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2.81k/2.81k [00:00<00:00, 1.91MB/s]
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3.29G/3.29G [01:00<00:00, 54.2MB/s]
```

## --gain

Accepts a percentage value between 0 and 1 for the model's information gain level during training. The closer to 0, the less knowledge is assimilated, but the faster the inference speed will be. The closer to 1, the more knowledge is assimilated, but the slower the inference speed will be. If the value is too close to 1, this may lead to **overfitting**, causing the model to memorize rather than learn.

```bash
sapilm --train /Users/User/Documents/datasets/data.txt --gain 0.5
```
```bash
[-------------------------------------------------------------------------- Training -------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2.09k/2.09k [00:00<00:00, 1.53MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 47.2MB/s]
```

## --name

Defines the filename for the model that will be generated as a result of the training.

```bash
sapilm --train /Users/User/Documents/datasets/data.txt --name model_name_3
```
```bash
[-------------------------------------------------------------------------- Training -------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2.81k/2.81k [00:00<00:00, 1.99MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 47.5MB/s]
```

```bash
sapilm --list
```
```bash
+----+---------------------+----------+----------+
| ID | MODEL               | EXT      | SIZE     |
+----+---------------------+----------+----------+
| 1  | default             | .model   | 10.00 GB |
| 2  | model_name_1        | .sapiens | 15.18 GB |
| 3  | model_name_2        | .sapiens | 14.31 GB |
| 4  | model_name_3        | .model   | 10.00 GB |
| 5  | model_name_N        | .sapiens | 28.97 GB |
+----+---------------------+----------+----------+
```

## --fit

Path to the dataset (exclusively in `JSON` format matching the Sapiens standard) used to apply a fine-tuning to a pre-trained model.

**Sapiens Standard JSON:** `{"data": [{"input": "string with a prompt sample...", "output": "string with a response sample..."}, ...]}` or `[{"input": "string with a prompt sample...", "output": "string with a response sample..."}, ...]`.


First, we will generate a base model to fine-tune later:

```bash
sapilm --train /Users/User/Documents/datasets/data.txt --name base_model_1
```
```bash
[------------------------------------------------------------------------- Training --------------------------------------------------------------------------]
Reading data [========================================================================================================================================] 100.00%
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 2.81k/2.81k [00:00<00:00, 1.99MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 47.5MB/s]
```

```bash
sapilm --load base_model_1 --fit /Users/User/Documents/datasets/data.json --name fit_model_1
```
```bash
Decoding: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████| 385M/385M [00:00<00:00, 413MB/s]
Decoding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.48k/1.48k [00:00<00:00, 4.28MB/s]
[------------------------------------------------------------------------ Fine-tuning ------------------------------------------------------------------------]
Adjusting: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 6/6 [00:00<00:00, 5379.61item/s]
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3.44k/3.44k [00:00<00:00, 1.10MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 48.7MB/s]
```

Note that you can apply fine-tuning to any model you have previously trained. Simply use the load command to load the model to be fine-tuned followed by the adjustment command on the same line.

```bash
sapilm --load base_model_N --fit /Users/User/Documents/datasets/data.json --name fit_model_N
```
```bash
Decoding: 100%|██████████████████████████████████████████████████████████████████████████████████████████████████████████████| 385M/385M [00:00<00:00, 413MB/s]
Decoding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████| 1.48k/1.48k [00:00<00:00, 4.28MB/s]
[------------------------------------------------------------------------ Fine-tuning ------------------------------------------------------------------------]
Adjusting: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 6/6 [00:00<00:00, 5379.61item/s]
Coding: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3.44k/3.44k [00:00<00:00, 1.10MB/s]
Coding: 100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████| 398M/398M [00:08<00:00, 48.7MB/s]
```

## --version

Displays the current version of SapiLM installed on your local machine. The same as `--v`.

```bash
sapilm --version
```
```bash
SapiLM 1.1.9
```

## --v

Displays the current version of SapiLM installed on your local machine. The same as `--version`.

```bash
sapilm --v
```
```bash
SapiLM 1.1.9
```

## Contributing

We do not accept contributions that may result in changing the original code.

Make sure you are using the appropriate version.

## License

This is proprietary software and its alteration and/or distribution without the developer's authorization is not permitted.
