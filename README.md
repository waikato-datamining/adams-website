# adams-website

Source code for the [ADAMS](https://adams.cms.waikato.ac.nz/) website.
Uses [Nikola](https://getnikola.com/), the static site generator.

## Nikola setup

* virtual environment

  ```bash
  virtualenv -p /usr/bin/python3 venv
  ```

* install packages and plugins

  ```bash
  ./venv/bin/pip install nikola micawber ruamel.yaml
  ./venv/bin/nikola plugin -i slides
  ```

## Build and deploy

* build and serve (locally)

  ```bash
  ./venv/bin/nikola clean && ./venv/bin/nikola build && ./venv/bin/nikola serve
  ```

* deploy

  ```bash
  ./venv/bin/nikola deploy
  ```
