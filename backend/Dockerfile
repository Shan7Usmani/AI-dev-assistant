FROM python:3.12-slim

WORKDIR /app

# Install dependencies
COPY backend/requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy backend source
COPY backend/ ./backend/

# Copy frontend
COPY frontend/ ./frontend/

WORKDIR /app/backend

EXPOSE 8000

# Use shell form so environment variables (like $PORT on Render) are expanded.
# Fall back to 8000 when PORT is not set.
CMD ["/bin/sh", "-c", "uvicorn app.main:app --host 0.0.0.0 --port ${PORT:-8000}"]