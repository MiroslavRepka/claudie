# Claudie `v0.6`

!!! warning "Due to a breaking change in the terraform files the `v0.6.x` will not be backwards compatible with `v0.5.x`"

## Deployment

To deploy Claudie `v0.6.X`, please:

1. Download the archive and checksums from the [release page](https://github.com/berops/claudie/releases)

2. Verify the archive with the `sha256` (optional)

    ```sh
    sha256sum -c --ignore-missing checksums.txt
    ```

   If valid, output is, depending on the archive downloaded

    ```sh
    claudie.tar.gz: OK
    ```

   or

    ```sh
    claudie.zip: OK
    ```

   or both.

3. Lastly, unpack the archive and deploy using `kubectl`

   > We strongly recommend changing the default credentials for MongoDB, MinIO and DynamoDB before you deploy it. To do this, change contents of the files in `mongo/secrets`, `minio/secrets` and `dynamo/secrets` respectively.

    ```sh
    kubectl apply -k .
    ```

## v0.6.0

### Features
- Updated network policies [#1016](https://github.com/berops/claudie/pull/1016)
- Support flex instances [#993](https://github.com/berops/claudie/pull/993)
- De-duplication of terraform templates [#1021](https://github.com/berops/claudie/pull/1021)
- Timestamp added as part of workflow when saved in mongoDB [#1019](https://github.com/berops/claudie/pull/1019)

### Bugfixes
- Resolved [#598](https://github.com/berops/claudie/issues/598)

### Other
- Fix unknown AMIs and regions in docs [#1009](https://github.com/berops/claudie/pull/1009)
- Update the Roadmap [#1020](https://github.com/berops/claudie/pull/1020)
- Add hardening section to docs [#1026](https://github.com/berops/claudie/pull/1026)
- Add updating section to docs [#1028](https://github.com/berops/claudie/pull/1028)


## v0.6.1

### Bugfixes
- Fallback to use Kube-Proxy with Cilium, due to problems with network traffic  [#1035](https://github.com/berops/claudie/pull/1035)


## v0.6.2

### Features
- Limits and Requests of each claudie-deployed pod were adjusted [#1055](https://github.com/berops/claudie/pull/1055)

### Bugfixes
- Clusters made out of static nodepools should be correctly destroyed [#1038](https://github.com/berops/claudie/pull/1038)
- Issue when the hashes of current and desired state wouldn't match after config build sucessfully  [#1041](https://github.com/berops/claudie/pull/1041)
- Wireguard is now removed from static nodepools when the config is deleted [#1059](https://github.com/berops/claudie/pull/1059)