# Support-Ticket-Classification-using-RAG-and-Gemini-API-

## **Project: Support Ticket Classification using RAG and Gemini API**

### **Description**

This project aims to classify customer support tickets into predefined categories using a Retrieval-Augmented Generation (RAG) approach combined with the Gemini API. The primary goal is to leverage the power of pre-trained large language models to provide accurate and actionable categorization of support tickets, enhancing customer service efficiency.

### **Approach**

1. **Data Preparation**:  
   * We start by defining example support tickets and a knowledge base that contains descriptions of each category.  
   * The support tickets are simple text inputs describing common issues that users might face.  
2. **Embedding Creation**:  
   * We use the `sentence-transformers` library to create embeddings for both the support tickets and the knowledge base.  
   * These embeddings allow us to measure the similarity between different pieces of text, which is crucial for our retrieval step.  
3. **Retrieval of Relevant Documents**:  
   * Using FAISS, we create a vector store of the knowledge base documents.  
   * For each support ticket, we retrieve the most similar documents from the knowledge base.  
4. **Prompt Creation and Response Generation**:  
   * We construct a generic prompt that includes the support ticket and the retrieved knowledge base context. This prompt can scale with the knowledge base as it grows and includes various types of tickets.  
   * Using the Gemini API, we generate a response that indicates the most likely category of the support ticket.  
5. **Similarity Scoring for Category Mapping**:  
   * We compute the cosine similarity between the generated text from the Gemini API and the knowledge base categories.  
   * The category with the highest similarity score is selected as the classification result.

### **Rationale**

* **Retrieval-Augmented Generation (RAG)**: Combining retrieval and generation leverages the strengths of both approaches. Retrieval ensures that the model has access to relevant context, while generation provides flexibility in handling varied inputs.  
* **Generic Prompt**: The prompt is designed to be generic and adaptable, allowing it to scale as the knowledge base grows and includes different types of support tickets.  
* **Zero-shot and Few-shot Approaches**: We tried both zero-shot and few-shot approaches. Given the small and simple nature of the current knowledge base, the zero-shot approach works effectively for the current state. As the knowledge base expands and becomes more complex, a few-shot approach may be more beneficial.

### **Results**

* The system accurately classifies support tickets into predefined categories, as demonstrated by the example tickets provided.  
* The output format clearly indicates the classified category, aiding in easy interpretation and action.

### **Potential Shortcomings**

* **Dependency on Embedding Quality**: The accuracy of the classification heavily depends on the quality of the embeddings generated. Inaccurate embeddings can lead to incorrect similarity scores.  
* **Model Limitations**: The performance of the Gemini API and the sentence transformer model can vary based on the complexity and nature of the support tickets.  
* **Scalability**: The current approach works well for a limited set of categories and support tickets. Scaling to a larger dataset may require optimization and additional computational resources.

### **Improvements**

* **Fine-tuning**: Fine-tuning the sentence transformer model on a domain-specific dataset can improve the quality of the embeddings.  
* **Expanded Knowledge Base**: Increasing the size and variety of the knowledge base can provide better context for retrieval and improve classification accuracy.  
* **Error Handling**: Implementing robust error handling mechanisms to manage cases where the model fails to generate a meaningful response or retrieves irrelevant documents.


