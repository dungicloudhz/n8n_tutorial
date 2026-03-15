# Rag chatbot basic
- create database vector
```sql
-- Enable the pgvector extension to work with embedding vectors 
create extension vector;

-- Create a table to store your documents 
create table documents (
id bigserial primary key,
content text, -- corresponds to Document.pageContent 
metadata jsonb, -- corresponds to Document. metadata
embedding vector(1536) -- 1536 works for OpenAI embeddings, change if needed
);
```
![](./create%20extension%20vector.png)
```sql
-- Create a function to search for documents
create function match_documents(
    query_embedding vectoßr(1536),
    match_count int default null,
    filter jsonb DEFAULT '{}'
) return table (
    id bigint,
    context text,
    metadata jsonb,
    similarity float
)
language plpgsql
as $$

``` 
**Step Create rag**
![](./step%20create%20rag.png)
- Giải thích embedding, document (default data loader), load specific data (tìm hiểu cấu hình metadata), text spliters (tìm hiểu 3 loại),