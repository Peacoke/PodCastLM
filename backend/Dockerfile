FROM python:3.12-slim

RUN apt-get update && apt-get install -y git ffmpeg && \
    apt-get clean && rm -rf /var/lib/apt/lists/*
RUN useradd -m -u 1000 user
USER user
ENV HOME=/home/user \
	PATH=/home/user/.local/bin:$PATH

# 设置工作目录
WORKDIR $HOME/app

COPY --chown=user requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY --chown=user . .

EXPOSE 7860

# 运行应用
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "7860"]
