FROM registry.access.redhat.com/ubi9/python-311

ENV LITELLM_CONFIG_PATH="/litellm.secrets.toml"

# Add application sources with correct permissions for OpenShift
USER 0
COPY . /app
WORKDIR /app

RUN chown -R 1001:0 ./
USER 1001
RUN pip install -r requirements.txt

EXPOSE 8080

CMD exec uvicorn main:app --host 0.0.0.0 --port 8080 --workers 10 
