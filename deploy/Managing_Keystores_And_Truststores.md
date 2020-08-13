# Managing Java Keystores and Truststores

This chapter depicts important information about managing Java keystores and truststores in a container based
WSO2 product deployment.

## Contents

The following will be discussed in detail in the document.

* [Asymmetric Encryption in WSO2 products](#asymmetric-encryption-in-wso2-products)
* [Manage Keystores and Certificate Truststores in Container Based Deployments](#manage-keystores-and-certificate-truststores-in-container-based-deployments)

### Asymmetric Encryption in WSO2 Products

WSO2 products use asymmetric encryption by default for ensuring trust and secure tranfer of data. For advanced details,
please refer the official WSO2 [documentation](https://docs.wso2.com/display/ADMIN44x/Using+Asymmetric+Encryption#UsingAsymmetricEncryption-setting_up_keystoresUsageofkeystoresinWSO2products).

[Java keystores and truststores](https://docs.wso2.com/display/ADMIN44x/Using+Asymmetric+Encryption#UsingAsymmetricEncryption-Understandingkeystoresandtruststores)
are used to store SSL certificates required for asymmetric encryption.

Please refer to the official WSO2 [recommendations](https://docs.wso2.com/display/ADMIN44x/Using+Asymmetric+Encryption#UsingAsymmetricEncryption-recommendationsRecommendationsforsettingupkeystoresinWSO2products)
for managing keystores prior to following this guide.

### Manage Keystores and Truststores in Container Based Deployments

As per aforementioned WSO2 [recommendations](https://docs.wso2.com/display/ADMIN44x/Using+Asymmetric+Encryption#UsingAsymmetricEncryption-recommendationsRecommendationsforsettingupkeystoresinWSO2products),
it is often required to customize the default, WSO2 product keystore and truststore in a production grade deployment.

The most recommended approach for introducing a custom keystore or a truststore to a container based deployment is by using
volume mounting to replace the default one with the custom one.

1. Prepare the custom Java keystore or truststore.

   Please follow the official guidelines for [creating a new keystore](https://docs.wso2.com/display/ADMIN44x/Creating+New+Keystores#CreatingNewKeystores-Creatinganewkeystore)
   or [adding a Certificate Authority signed certificate to an existing keystore](https://docs.wso2.com/display/ADMIN44x/Creating+New+Keystores#CreatingNewKeystores-ca_certificateAddingCA-signedcertificatestokeystores)
   as per your preference.
   
   To import certificates to a truststore, follow the official [documentation](https://docs.wso2.com/display/ADMIN44x/Creating+New+Keystores#CreatingNewKeystores-Step3:Importingcertificatestothetruststore).
   
2. Add the keystore to the product container via a volume mount depending on the container platform.

   We recommend you to use the volume mount allocated for non-configuration resources in WSO2 product containers
   (i.e. `/home/wso2carbon/wso2-artifact-volume`) for this purpose.
   
   In Carbon Kernel **version 4** based products, the default `wso2carbon.jks` keystore is located at the
   `<WSO2_PRODUCT_HOME>/repository/resources/security` directory. Thus, you may mount the volume containing the
   custom keystore to `/home/wso2carbon/wso2-artifact-volume/repository/resources/security` directory.
   
   In Carbon Kernel **version 5** based products, the default `wso2carbon.jks` keystore is located at the
   `<WSO2_PRODUCT_HOME>/resources/security` directory. Thus, you may mount the volume containing the custom keystore
   to `/home/wso2carbon/wso2-artifact-volume/resources/security` directory.
   
3. Add the truststore to the product container via a volume mount depending on the container platform.

   We recommend you to use the volume mount allocated for non-configuration resources in WSO2 product containers
   (i.e. `/home/wso2carbon/wso2-artifact-volume`) for this purpose.
   
   In Carbon Kernel **version 4** based products, the default `client-truststore.jks` truststore is located at the
   `<WSO2_PRODUCT_HOME>/repository/resources/security` directory. Thus, you may mount the volume containing the
   custom keystore to `/home/wso2carbon/wso2-artifact-volume/repository/resources/security` directory.
   
   In Carbon Kernel **version 5** based products, the default `client-truststore.jks` truststore is located at the
   `<WSO2_PRODUCT_HOME>/resources/security` directory. Thus, you may mount the volume containing the custom keystore
   to `/home/wso2carbon/wso2-artifact-volume/resources/security` directory.
    
   > In Kubernetes based WSO2 product deployments, it is advisable that you use a ConfigMap resource to mount the custom keystore
   > and truststore.
   >
   > **Note:** Support for including binary data in Kubernetes ConfigMaps was introduced in version [`1.10`](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.10.md#apps).
   > 
   > For further understanding peruse:
   >
   > 1. [Create a ConfigMap resource from the keystore file](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#create-configmaps-from-files)
   >
   > 2. [Add the ConfigMap data to a volume](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#add-configmap-data-to-a-volume)
