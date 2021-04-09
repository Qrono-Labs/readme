# Qrono
Building logistics infrastructure for the internet -- starting with bookable assets.

This is our monolithic backend repo, in Django.


## Quickstart
1. Clone the source
`git clone git@github.com:ajroberts0417/qrono.git`

2. Navigate into the project directory
`cd qrono`

3. Install dependencies (if you don't have pipenv and python installed, go to [Installing Python](#installing-python))
`pipenv install`

4. Enter the pipenv virtual environment
`pipenv shell`

5. Run the bot:
`python manage.py runserver`

Boom! It's that easy -- you're now running Qrono locally.


## Contributing Code

- New commits should always be proposed in a [Pull Request](https://help.github.com/articles/about-pull-requests/)
- Every Pull Request requires at least one approval before merging
- Each Pull Request should be merged by the author after approval and CI checks
- Python code should follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) as closely as possible
- JavaScript code should be written as [TypeScript](https://www.typescriptlang.org/)
- Pull requests should clearly describe changes in dependencies
- See [styleguide_example.py](https://github.com/ajroberts0417/qrono/blob/master/styleguide_example.py) for an opinionated example on how to document and type python code

We use [Black](https://pypi.org/project/black/#:~:text=Black%20is%20the%20uncompromising%20Python,energy%20for%20more%20important%20matters.) for code formatting.
Before submitting code run: `pipenv run black .` to autoformat your code.


## Dependencies
- A version of python 3.9 installed and added to your PATH (for help: [install python 3](https://www.codecademy.com/articles/install-python3))
- A version of [pipenv](https://pypi.org/project/pipenv/) installed
- [Postgresql](https://www.postgresql.org/)


## Installing Python
Managing python environments can be tricky, even for experienced developers. One easy tool to do so is [pyenv](https://github.com/pyenv/pyenv).
Here's how you can use a python 3.9 environment in your `qrono` directory:

1. Install pyenv (see [pyenv installer](https://github.com/pyenv/pyenv-installer))
`curl https://pyenv.run | bash` 

1b.  Restart your shell so the changes take effect:
`exec $SHELL`

2. Install the latest version of python 3.9 using pyenv
`pyenv install 3.9.2`

3. Use this version locally in your qrono project
(Note: make sure you're in the `qrono` directory!)
`pyenv local 3.9.2`

3b. Alternatively, if you want 3.9.2 to be your global version of python:
`pyenv global 3.9.2`

4. Install the latest version of pipenv:
`pip install pipenv`

### Troubleshooting Python Installs
##### OpenSSL

Openssl is a dependency for `psycopg2`, and the installation might fail if the linked library isn't the right version. If this command fails with clang error 1—and you are on macOS—ensure Xcode is installed with `xcode-select --install` and ensure openssl is linked by running:

```sh
env LDFLAGS="-I/usr/local/opt/openssl/include -L/usr/local/opt/openssl/lib" make install-dev
```

If this command fails with clang error 1 and `error: architecture not supported`, add the `ARCHFLAGS` option as well:

```sh
env LDFLAGS="-I/usr/local/opt/openssl/include -L/usr/local/opt/openssl/lib" ARCHFLAGS="-arch i386 -arch x86_64" make install-dev
```
