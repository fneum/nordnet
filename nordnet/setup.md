# Installation

## Google Colab (recommended)

You can begin with the course without a local Python installation using online
services like  [Google Colab (colab.google)](https://colab.google) which provide
an online Python version in a [Jupyter Notebook](jupyter.org/) environment. **This
requires a Google account.**

To import a notebook, navigate to the other pages of this website.
You will find a download button at the top of each page.
Download the `.ipynb` file and import it in Google Colab.

## Local Installation using `uv` (optional)

### Download Repository

For these options it makes sense to *clone* the repository to your laptop. You can do this by running:

```sh
git clone https://github.com/fneum/nordnet.git
```

or by downloading the repository as a ZIP file (look for a green "Code" button) and extracting it to a local folder:

https://github.com/fneum/nordnet

Then, navigate to the `nordnet` directory where you will find the `.ipynb` files for the course materials.

```
cd nordnet
```

## Install `uv`

For using `uv` as package manager, first follow the [installation instructions](https://docs.astral.sh/uv/getting-started/installation/). These differ depending on your operating system.

You can check the installation by running `uv --version` in the console.

### Start Jupyter Lab

Once `uv` is installed, navigate to your local copy of the course repository in the console and start a new Jupyter Lab session in your browser:

```sh
uv run jupyter lab
```

This will automatically install the required packages in a virtual environment. However, it is important that you run this command in the root folder of the course repository, where the `pyproject.toml` and `uv.lock` files are located.
