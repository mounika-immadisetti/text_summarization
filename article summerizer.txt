# -------------------------------
# ARTICLE SUMMARIZATION TOOL
# -------------------------------

from transformers import pipeline

def summarize_text(article, max_length=130, min_length=30):
    """
    Summarizes the given article using a pre-trained transformer model.
    Parameters:
        article (str): Input text/article to summarize.
        max_length (int): Maximum length of summary.
        min_length (int): Minimum length of summary.
    Returns:
        str: Summarized text.
    """
    summarizer = pipeline("summarization", model="facebook/bart-large-cnn")
    summary = summarizer(article, max_length=max_length, min_length=min_length, do_sample=False)
    return summary[0]['summary_text']


if _name_ == "_main_":
    print("=== ARTICLE SUMMARIZATION TOOL ===\n")
    # Example Input Text
    article = """
    Artificial Intelligence (AI) is transforming industries around the world.
    It enables machines to learn from data and perform tasks that normally require human intelligence,
    such as recognizing speech, making decisions, and translating languages.
    With advancements in deep learning and neural networks, AI is becoming increasingly powerful and accessible.
    Many organizations are now using AI to improve efficiency, enhance customer experience, and gain competitive advantage.
    However, the rise of AI also raises ethical concerns about privacy, bias, and job displacement.
    """

    print("Original Article:\n", article)
    print("\nGenerating Summary...\n")

    summary = summarize_text(article)
    print("Summary:\n", summary)