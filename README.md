# Summary

Project for issue of Nuitka: `AttributeError: type object 'h5py.h5.H5PYConfig' has no attribute '__reduce_cython__'` 

# Project Setup

~~~shell
cd <project directory>
python3 -m venv venv
source venv/bin/activate
pip install rasa==2.6.2 spacy==3.0.6 awscrt
python -m spacy download de_core_news_md --no-deps
~~~

# Nuitka Build

~~~shell
sudo apt install chrpath ccache
source venv/bin/activate
python -m pip install nuitka
python -m nuitka --follow-imports --plugin-enable=tensorflow --plugin-enable=pylint-warnings --plugin-enable=numpy --onefile venv/bin/rasa
~~~

# Run

~~~shell
cp rasa.bin /tmp
cp -r models /tmp
cd /tmp
./rasa.bin run -m models
~~~
