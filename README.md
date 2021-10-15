# adams-website

Source code for the [ADAMS](https://adams.cms.waikato.ac.nz/) website.
Uses [Nikola](https://getnikola.com/), the static site generator.

## Nikola setup

* virtual environment

  ```commandline
  virtualenv -p /usr/bin/python3 venv
  ```

* install packages and plugins

  ```commandline
  ./venv/bin/pip install nikola micawber
  ./venv/bin/nikola plugin -i slides
  ```

## Build and deploy

* build and serve (locally)

  ```commandline
  ./venv/bin/nikola clean && ./venv/bin/nikola build && ./venv/bin/nikola serve
  ```

* deploy

  ```commandline
  ./venv/bin/nikola deploy
  ```
