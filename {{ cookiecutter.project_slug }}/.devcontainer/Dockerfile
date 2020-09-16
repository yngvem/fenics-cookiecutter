FROM quay.io/fenicsproject/stable:current

# Requirements for codebase
COPY requirements.txt /tmp/requirements.txt
COPY requirements-upgrade.txt /tmp/requirements-upgrade.txt
RUN pip install --upgrade -r /tmp/requirements.txt
RUN pip install --upgrade -r /tmp/requirements-upgrade.txt
RUN rm /tmp/requirements.txt
RUN rm /tmp/requirements-upgrade.txt

# Install jupyter
RUN pip install --upgrade jupyter_contrib_nbextensions jupyter_nbextensions_configurator

RUN jupyter notebook --generate-config
RUN jupyter contrib nbextension install --system
RUN jupyter nbextensions_configurator enable --system
RUN echo "c.NotebookApp.ip = '0.0.0.0'\n" >> /root/.jupyter/jupyter_notebook_config.py
RUN echo "c.NotebookApp.allow_root = True\n" >> /root/.jupyter/jupyter_notebook_config.py