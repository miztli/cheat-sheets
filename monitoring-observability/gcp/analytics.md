### Log query sample

```sql
-- SELECT * FROM( 
--SUM(total_hits) FROM(
SELECT
 -- timestamp,
 -- json_payload.message,
 REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'query=([^,)]+)') AS query_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'skipAutoCorrect=([^,)]+)') AS skip_autocorrect_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'skipRedirect=([^,)]+)') AS skip_redirect_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'startIndex=([^,)]+)') AS start_index_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'itemsPerPage=([^,)]+)') AS items_per_page_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'selectedFilters=([^,)]+)') AS selected_filters_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'selectedSort=([^,)]+)') AS selected_sort_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'basketSKUs=([^,)]+)') AS basket_skus_value,
 REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'categoryKeys=\[([^\]]*)\]') AS category_keys_value,
  REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'BRAND=\[([^\]]*)\]') AS brand_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'personalizationEnabled=([^,)]+)') AS skip_autocorrect_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'sponsoredProductEnabled=([^,)]+)') AS skip_autocorrect_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'pageType=([^,)]+)') AS page_type_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'experience=([^,)]+)') AS experience_value,
 -- REGEXP_EXTRACT(JSON_VALUE(json_payload.message), r'platform=([^,)]+)') AS platform_value,
 -- *,
  -- Extracts the content inside the brackets [UltaSearchRequest(...)]
  -- REGEXP_EXTRACT(json_payload.message, r'\[(.*)\]') as search_request,
  -- REGEXP_EXTRACT(json_payload.message, r'query=([^,]+)') AS search_query,
  -- receive_timestamp,
  --resource.labels.cluster_name,
  --resource.labels.container_name,
  --resource.labels.location,
  --resource.labels.namespace_name,
  --resource.labels.project_id
  count(*) as total_hits
FROM
  `ulta-dsp-prod.global._Default._AllLogs`
WHERE
  -- Using your current filters
  timestamp >= TIMESTAMP("2026-05-04 14:50:00", "America/Mexico_City") 
  AND timestamp <= TIMESTAMP("2026-05-04 14:50:59", "America/Mexico_City") 
  -- timestamp >= TIMESTAMP("2026-05-05 23:00:00", "America/Chicago") 
  -- AND TIMESTAMP("2026-05-05 23:59:59", "America/Chicago")
  -- timestamp > TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 1 MINUTE)
  AND resource.type = "k8s_container"
  AND JSON_VALUE(resource.labels.location) = "us-central1"
  -- AND JSON_VALUE(resource.labels.namespace_name) = "guest-b"
  AND JSON_VALUE(resource.labels.container_name) = "v1-orch-shop-productsearch" 
  AND STARTS_WITH(JSON_VALUE(json_payload.message), "UltaSearchServiceImpl : searchProductsByKeywords :: searchRequest :")
  -- AND starts_with(json_payload.message , "UltaSearchServiceImpl : searchProductsByKeywords :: searchRequest :")
  -- AND timestamp > TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 1 MINUTE)
  GROUP BY query_value, category_keys_value, brand_value
  -- experience_value, platform_value
  --HAVING COUNT(*) >= 10
  ORDER BY total_hits desc
  --)
  -- where query_value is null 
  --and category_keys_value is null 
  -- and brand_value is null
  ;
```