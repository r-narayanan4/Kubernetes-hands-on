#Commands to create certificate

#Command to create private key for user
#Generate a private key

 openssl genrsa -out ravi.key 2048

#Command to create certificate signing request

#Create a certificate signing request

openssl req -new -key ravi.key -out ravi.csr -subj "/CN=ravi/O=ravi.org"
openssl req -new -key ravi.key -out ravi.csr -subj "/CN=ravi/o=dev/O=ravi.org"
#Command to sign by certificate authority we must have ca.crt and ca.key it presented in /etc/kubernetes/pki/ca.crt: Certificate Authority (CA) certificate. and /etc/kubernetes/pki/ca.key: Certificate Authority (CA) private key.
#Sign the certificate with a certificate authority

openssl x509 -req -in ravi.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out ravi.crt -days 500


#To create user using the certificate use the below cmd 

kubectl config set-credentials rln --client-certificate=rln.crt --client-key=rln.key

kubectl config set-credentials rvl --client-certificate=rln.crt --client-key=rln.key

kubectl config set-credentials ravi --client-certificate=rln.crt --client-key=rln.key

#To create context for the user

kubectl config set-context rln --cluster=kubernetes --user=rln  --namespace=default


#If you want to delete credentials 

kubectl config unset users.rln


#if you want to delete context

kubectl config delete-context rln

#if you want to get contexts

kubectl config get-contexts


#if you want to get credentials 

kubectl config view --minify --output jsonpath='{range .users[*]}{.name}{"\n"}{end}'

or see kube/config file

#To switch the context 

kubectl config use-context <context_namne>
kubectl  config use-context rln
