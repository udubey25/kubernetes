#Readme
#Create a key using openssl on workstation machine
#--> openssl genrsa -out workstation.key 2048
#Create a csr using this key
#--> openssl req -new -key workstation.key -out workstation.csr
#Copy the CSR and the key to the manager node
#Generate the certificate using the root CA and the csr file
#--> openssl x509 -req -in utkarsh.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out utkarsh.crt -days 1000
#Copy this certificate back to the workstation machine
#Now create a credential for this user on the manager node with the newly created certificate and csr
#--> kubectl config set-credentials utkarsh --client-certificate=utkarsh.crt --client-key utkarsh.key
#Create a role and rolebinding using the above yaml for the same.
#Update the config file after taking the backup by updating the users and contexts section. Copy this file to the home directory of the respecctive user on the workstation machine under .kube directory
