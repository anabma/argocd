# ArgoCD + Traefik + cert-manager (Technitium DNS01) — Fixed Manifests

Apply in this order (Argo CD will handle waves if these are Applications inside Argo CD):

1. 01-traefik-application.yaml
2. 02-cert-manager-application.yaml
3. 03-technitium-webhook-application.yaml
4. 04-technitium-api-token-secret.yaml  (EDIT the token before applying)
5. 05-cluster-issuer-staging.yaml
6. (Optional) 06-cluster-issuer-prod.yaml (switch to prod when staging works)
7. 07-argocd-certificate.yaml
8. 08-argocd-ingress.yaml

Notes:
- Replace `REPLACE_WITH_TECHNITIUM_API_TOKEN` in the Secret with your real token.
- All NGINX-specific manifests (ingress-nginx controller, nginx annotations) were replaced with Traefik equivalents.
- The Ingress/Certificate live in the `argocd` namespace and use the same `secretName: argocd-tls`.
- ClusterIssuers are cluster-scoped and therefore have no namespace.
- Staging is used by default to avoid rate limits; switch the Ingress and Certificate annotations/issuerRef to the prod issuer when ready.


---
Wildcard TLS (optional, for shared cert across apps):
9.  09-wildcard-cert-staging.yaml
10. 10-wildcard-cert-prod.yaml
11. 11-traefik-tlsstore.yaml (uses secretName: wildcard-tls in traefik namespace)
