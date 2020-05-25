# Pandoc Docker Container

Dieses Repo stellt ein Docker-Image zur Verfügung mit dem Dokumente sehr einfach von Markdown nach LaTeX oder PDF umgewandelt werden können.

In `example` ist mal ein Beispiel mit verschiedenen Möglichkeiten zu finden.

Das ganze ist noch nicht sehr intuitiv. Wir arbeiten dran...

## Installation

```sh
# Repo clonen
git clone https://github.com/hd-code/pandoc-docker.git

# In den Ordner wechseln
cd pandoc-docker

# Docker Image bauen
docker build -t pandoc .
```

Nun kann die Software verwendet werden.

_Hinweis:_ Die volle LaTeX Software ist um die 5GB groß, also nicht wundern, wenn die Installation sehr lange braucht und viel Speicher belegt. Herr Avemarg und ich sind schon dabei, das zu reduzieren. Aber mit der Vollversion ist man erstmal immer auf der sicheren Seite.

## Usage

```sh
# md to pdf
docker run --rm -it -v '$PWD':/data pandoc pandoc [markdown-file].md -o [output-file].pdf

# md to pdf + bibtex
docker run --rm -it -v '$PWD':/data pandoc pandoc [markdown-file].md -o [output-file].pdf --bibliography [bibtex-file].bib

# md to latex
docker run --rm -it -v '$PWD':/data pandoc pandoc [markdown-file].md -o [output-file].tex

# latex to pdf
docker run --rm -it -v '$PWD':/data pandoc pdflatex [latex-file].tex
```