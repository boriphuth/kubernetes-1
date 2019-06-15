## 1. Pulling private images

Create kubernetes secrets 

```
kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-userme=kammana --docker-password=<your-password> --docker-email=hari.kammana@gmail.com
```
After create secret, lets create pod which uses private images.

```
apiVersion: v1
kind: Pod
metadata:
  name: private-reg
spec:
  containers:
  - name: privateapp
    image: kammana/privateapp:0.0.1
  imagePullSecrets:
  - name: regcred

```