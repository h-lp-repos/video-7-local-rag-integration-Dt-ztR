# Video 7: Integración RAG Local

## Objetivo
Integrar recuperación basada en FAISS local dentro de un demo de RAG, reemplazando las llamadas a embeddings en la nube, y ejecutar 3 consultas end-to-end.

Este video muestra cómo construir un pipeline de Retrieval-Augmented Generation completamente local, eliminando dependencias externas y costos de inferencia en la nube.

## Pasos

1. Localizar y abrir el script de integración RAG:
   ```bash
   cat retrieval_integration.py
   ```

2. Reemplazar las llamadas a embeddings cloud por:

   * Inferencia local de embeddings
   * Búsqueda k-NN usando el índice FAISS local

3. Ejecutar el pipeline end-to-end:

   ```bash
   python retrieval_integration.py \
     --queries queries.json \
     --index ../video-5-build-faiss-index-knn-retrieval/index.faiss \
     --out run_output.json
   ```

4. Revisar los resultados generados:

   ```bash
   cat run_output.json
   ```

5. (Opcional) Revertir los cambios del script:

   ```bash
   git checkout -- retrieval_integration.py
   ```

## Solución de problemas

* **Errores de mapeo de IDs**: verificá que `retrieved_doc_ids` coincidan correctamente con los IDs del corpus.
* **Falta de API key**: utilizá `generator_stub.py` para evitar dependencias externas durante la generación.
