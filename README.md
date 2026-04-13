

**Rahul kumar (rahul.kumar@rapidfort.com)**

**Total tickets resolved : 90+**

---

## Learning so far :

- CVEs remediation
- Binary discovery and filesystem analysis within containers
- How multistage dockerfile proceed in terms of execution
- Transitive dependencies can downgrade the pinned version
- How to write multistage dockerfile

---

## CONTRIBUTIONS :

### Steps for creating new image

1. Analyse the original dockerfile  
2. Build the binaries from scratch and do not copy directly from prebuilt binaries  
3. check dynamic linking in case of FIPS images  
4. remove cache, tmp, metadata files to keep the image size minimal  
5. prune the set uid and gid to remove any possible root privileges in there.  
6. For FIPS, enable strict fips mode by default  
6. In the final stage set the required workdir, path, cmd and entrypoint in accordance with original dockerfile.  

---

### New Images :

- openebs/linux-utils (under review)
- fluxcd/helm-operator
- minio/operator (bitnami section)

---

### Steps for Vbumps

1. take a look at the changes in original dockerfile  
2. look at the release for changes, bug fixes and features  
2. change dockerfile as per the new original dockerfile  
3. use unpatch/patch strategy to check if some cve is already patched in Vbump  

---

### Version bumps :

- grafana/alloy :: 1.10.2 -> 1.14.2  
- otel/opentelemetry-collector-contrib :: 0.148.0 -> 0.149.0  
- nginx/nginx-ingress :: 5.4.0 -> 5.4.1  
- jkroepke/kube-webhook-certgen :: 1.7.9 -> 1.8.0  
- k8s-dns-node-cache :: 1.26.7 -> 1.26.8  
- rancher/hardened-cni-plugins :: 1.9.0 -> 1.9.1  
- grafana/pyroscope :: 1.18.1 -> 1.20.0  
- csi-secrets-store/driver :: 1.5.5 -> 1.5.6  
- prometheuscommunity/pgbouncer-exporter :: 0.11.0 -> 0.12.0  
  7+ other apps  

---

### Steps for CVE remediation:

1. Scan the image to find the CVE  
2. Search for the CVE and look into advisories to make sure it's not a false-positive case.  
3. look at the rf advisory to know the cve details (version and binary )  
4. use the dependency update command as per the requirement to update the package.  
5. If the CVE still persists, then check of any trannsitive dependency and use edit replace if any particular version is pinned in the go.mod(as replace)  

---

### CVEs remediation in images :

- grafana/alloy  
- daprio/daprd  
- daprio/injector  
- daprio/operator  
- grafana/pyroscope  
- minio/minio  
- minio/operator  
- minio/sidecar  
- traefik  
  7+ other apps  

---

## New tools learn :

- k9s  
- new git-based commands (stash, reset, blame, git mv etc.)  
- Dockerfilegraph
- dive
