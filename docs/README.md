# OPT Documentation

Public and internal documentation for Low codes improvement for MMP M&S. This repo is open to everyone in Equinor. **It must not contain any secrets or restricted information.**

It consists of two different documentation sites created using `mkdocs`:

* `public`, available on ?
* `internal`, available on ?

## Run ``mkdocs`` locally

Running mkdocs requires that you have [Python](https://wiki.equinor.com/wiki/index.php/Software:Python) installed and working.

1. Clone this repository:

```console
git clone https://github.com/equinor/improvement-disc
cd improvement-disc/docs/public # 
```

1. Install Python dependencies from requirements.txt

```console
pip install -r requirements.txt
```

1. Run mkdocs

```console
mkdocs serve
```


```

## Credits

* `mkdocs` configuration and theme stolen from [equinor/prix-internal](https://github.com/equinor/prix-internal)
* Dockerfile stolen from [equinor/thelma-docs](https://github.com/equinor/thelma-docs)