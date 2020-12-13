# Errores PKIX

### Ruta del cacerts incorrecta

**Motivo:** No se tiene acceso al certificado remoto, no se han agregado los certificados al almacén de java o no se tiene acceso al almacén.

**Solución:** Agregar certificados y/o agregar código Java para indicar donde se encuentra el almacén de certificados, así como la contraseña para acceder a él, asegurándose que se tienen permisos del servidor de aplicaciones para acceder a él y que la red está abierta para llegar a la url de los certificados.

**Traza de error** ([traza  completa](https://github.com/kioz-developer/cacerts/blob/master/errores/invalid_path_1.log))
> javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
> Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty

> Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty

> javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty

> Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty

### La contraseña de acceso al almacén de certificados es incorrecta

**Traza de error** ([traza  completa](https://github.com/kioz-developer/cacerts/blob/master/errores/invalid_pwd.log))
> javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: No X509TrustManager implementation available

> Caused by: java.security.cert.CertificateException: No X509TrustManager implementation available

> javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: No X509TrustManager implementation available

> Caused by: java.security.cert.CertificateException: No X509TrustManager implementation available

### Almacén no contiene el certificado correspondiente ó se tiene un bloqueo a nivel de red

**Motivo:** El almacén no contiene el certificado o existe un bloqueo en la red.

**Solución:** Se tienen que revisar las reglas del firewall, no es suficiente con hacer un curl o un wget.

**Traza de error** ([traza  completa](https://github.com/kioz-developer/cacerts/blob/master/errores/network_blocked.log))
> javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

### La ruta del archivo cacerts es incorrecta

**Motivo:** La ruta indicada en el javax.net.ssl.trustStore no es la correcta.

**Solución:** Apuntar a la ruta correcta del cacerts, no apuntar únicamente a la carpeta.

**Traza de error** ([traza  completa](https://github.com/kioz-developer/cacerts/blob/master/errores/invalid_path_2.log))

> org.springframework.web.client.ResourceAccessException: I/O error on GET request for "[YOUR_SERVICE_URL]": sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target; nested exception is javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target

> Caused by: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target
