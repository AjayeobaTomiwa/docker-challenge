FROM python:3.10

# create container working directory
WORKDIR /app

# update and install installation tools]
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

# poetry install
RUN curl -sSL https://install.python--poetry.org | python3 -

# adding poetry to PATH
ENV PATH="/root/.local/bin:$PATH"

# copy application code to current container directory
COPY . .

# install dependencies w/ poetry
RUN poetry install

# set executable permission for prestart script
RUN chmod +x ./prestart.sh

# expose app port
EXPOSE 8000

# Run prestart script and start server using poetry
CMD ["sh", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload"]