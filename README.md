Proprietary software developed by Sapiens Technology®️, used to manage, train, fine-tune, and infer language models of the Sapiens family.

# SapiLM

The SapiLM is proprietary software developed by Sapiens Technology®️, created to manage, train, fine-tune, and infer language models of the Sapiens family. It has various features that facilitate the development and deployment of models with the SAPI (Semantic AI with Pretrained Integration) architecture, such as functions for loading, listing, deleting, and repairing models, functions for base training, continuous training, fine-tuning, and inference, as well as functions for downloading and validation. The internal system of SapiLM also provides a native API with rotes and endpoints ready for production use.

![SAPI](sapilm.png)

## Recommendation

Install Python 3.11 and create a virtual environment with that version.

Here's an example of how to do this on Linux or Mac:
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

Update the pip package manager:
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
pip install sapilm-1.0.4-py3-none-any.whl
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

## Contributing

We do not accept contributions that may result in changing the original code.

Make sure you are using the appropriate version.

## License

This is proprietary software and its alteration and/or distribution without the developer's authorization is not permitted.
