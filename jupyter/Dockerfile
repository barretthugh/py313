FROM barretthugh/py313

COPY jupyter/requirement.txt /requirement.txt
COPY jupyter/jupyter_notebook_config.py /root/.jupyter/

RUN apt-get update \
  && apt install -yqq libpq-dev \
  && pip install -r /requirement.txt 

WORKDIR "/"

RUN apt-get purge --auto-remove -yqq $buildDeps \
    && apt-get autoremove -yqq --purge \
    && apt-get clean \
    && rm -rf \
        /var/lib/apt/lists/* \
        /tmp/* \
        /var/tmp/* \
        /usr/share/man \
        /usr/share/doc \
        /usr/share/doc-base \
        /var/cache/*

EXPOSE 8888
CMD ["jupyter", "lab", "--allow-root"]