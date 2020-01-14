# Utils-Config
Library to use .json files as configuration objects using namedtuple.

This library let's you use `.json` files as "objects" within your code.

## Installation

```console
pip install git+https://github.com/yeyeto2788/Utils-Config
```

## Usage

Create a file called `config.json` (you can change the name to something you like) and add some content to it.

In this demo we add the following data:
```json
{
  "temperature": 30,
  "screen": {
    "width": 640,
    "height": 480 
  },
  "name": null,
  "id": "4V3RYCR4ZY1D"
}
```

Now let's head over Python and test the module and its functions.

Importing the module and loading our `.json` file. 
```python
import utils_config

config_file = "./config.json"

config = utils_config.load_config(config_file)
```

Now let's see what we've got in the `config` variable, serializing it into a dictionary.
```python
utils_config.serialize_config(config)
```

Let's access to its keys/attributes.
```python
config.temperature
config.screen.width
config.name
config.id
```

Edit the current configuration (Take into account that this function will return a new `configuration` namedtuple)
```python
config = utils_config.edit_config(config, {"id": "another_id"})
config.id
```

Save the configuration to a file.
```python
utils_config.save_config(config_file, config)
```


## Contributing

**All contributions, pull requests and comments are welcome!**

When contributing it is important to test the module in order to make sure
everything is working as expected. For that install dependencies to run the tests.

```console
pip install pytest pytest-cov mock pylint
```

Running tests and see coverage.

```console
py.test --cov -v --cov-config=.coveragerc --cov-report=html
```

This will generate a report with the coverage which is at **100%** now, let's try to keep
it at the same percentage.