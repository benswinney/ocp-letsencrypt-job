# OpenShift Let's Encrypt Job (AWS & CloudFlare)

A `Job` that runs the Acme.sh script to generate Let's Encrypt certs for the "api" endpoint of your OpenShift cluster, as well as the "apps" wildcard subdomain.

To run:

Clone this repo and update either the "job/aws/cloud-dns-credentials-aws.yaml" secret for AWS (a user with Route53 permissions should do fine) or "job/cloudflare/cloud-dns-credentials-aws.yaml" for CloudFlare.

Apply the common manifests

```bash
oc apply -k common
```

Apply the job related to your DNS provider.

  AWS:

  ```bash
  oc apply -k job/aws
  ```

  CloudFlare:

  ```bash
  oc apply -k job/cloudflare
  ```

Done!

This will take a few minutes, but once the job succeeds, you should have good certs for your api endpoint as well as wildcard cert for your "apps" domain.
