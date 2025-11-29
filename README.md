Intelligent Bill Extraction API
This solution is a high-accuracy, AI-powered API designed to extract line item details from complex, multi-page invoices (PDFs and Images). It leverages GPT-4o (Multimodal) to visually analyze documents, ensuring accurate extraction even from messy layouts while preventing double-counting.
🚀 Features
Multimodal Extraction: Handles both PDF documents and Image files (JPG/PNG).
Intelligent Deduplication: Distinguishes between "Detailed" pages and "Final Summary" pages to avoid double-counting items.
Strict Schema Compliance: Returns data in the exact JSON format required by the problem statement.
Robust Math: Extracts Unit Rate, Quantity, and Net Amount.
🛠 Tech Stack
FastAPI: High-performance web framework.
OpenAI GPT-4o: State-of-the-art Vision language model.
Poppler / pdf2image: For rendering PDF pages into images for AI analysis.
Docker: Containerized for easy deployment.
📦 How to Deploy
Option 1: Railway (Recommended)
Fork/Clone this repository to your GitHub.
Login to Railway.app.
Create a New Project > Deploy from GitHub Repo.
Go to Variables and add:
OPENAI_API_KEY: sk-...... (Your OpenAI Key)
Go to Settings > Networking and click Generate Domain.
Option 2: Run Locally
Install system dependencies (Poppler):
Mac: brew install poppler
Linux: sudo apt-get install poppler-utils
Install Python libs:
pip install -r requirements.txt


Set your API key in a .env file.
Run:
uvicorn main:app --reload


🔗 API Usage
Endpoint: POST /extract-bill-data
Request Body:
{
  "document": "[https://hackrx.blob.core.windows.net/assets/datathon-IIT/sample_2.png](https://hackrx.blob.core.windows.net/assets/datathon-IIT/sample_2.png)..."
}


Response:
Returns is_success, token usage, and the structured pagewise_line_items.
