# hsa-nginx-fine-tuning
Nginx Fine Tuning

## How to start
1. Clone the repo to local machine
2. Run `docker-compose up -d`

## How to test
1. Head to `localhost:777/lev.jpeg` or `localhost:777/hippo.jpeg`
2. Examine network for response header `X-Cache-Status`, if requested image was requested at first - it will be `MISS`, otherwise - `HIT`
   1. ![](proofs/lev_requested_miss.png)
   2. ![](proofs/lev_requested_hit.png)
   3. ![](proofs/hippo_requested_miss.png)
   4. ![](proofs/hippo_requested_hit.png)
3. Run shell script `change-images.sh`
4. Head to given URIs(any) and examine header `Test`
   1. `localhost:777/purge_cache?target=lev.jpeg` ![](proofs/cache_purge_lev.png) 
   2. `localhost:777/purge_cache?target=hippo.jpeg` ![](proofs/cache_purge_hippo.png) 
   3. `localhost:777/purge_cache/all` ![](proofs/cache_purge_all.png)
5. After that head again for original images, their content should change and cache itself again after 1st use
