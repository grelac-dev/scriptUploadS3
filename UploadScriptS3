import paramiko
import os
import botocore.exceptions
import boto3

from paramiko import Transport, SFTPClient, RSAKey, SSHClient
import os

#abra o transporte
con = Transport('Ip Servidor',22) 
myuser = " Usuario Servidor"
#private_key = RSAKey(filename='/home/carlos/Documents/certs/key.pem') caso for chave ssh descomentar essa linha
passwordSSH = "Senha Servidor"



ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())

con.connect(None,username=myuser,password=passwordSSH)
sftp = SFTPClient.from_transport(con)
sftp.get('local do arquivo Raiz /home/server/Script/arquivo.zip', 'maquina que vai receber o Dowload /home/carlos/Script/arquivo.zip')
sftp.close()

ssh.close()
 
 
from botocore.exceptions import NoCredentialsError

ACCESS_KEY = 'Acess key AWS'
SECRET_KEY = 'Secret key AWS'


def upload_to_aws(local_file, bucket, s3_file):
    s3 = boto3.client('s3', aws_access_key_id=ACCESS_KEY,
                      aws_secret_access_key=SECRET_KEY)

    try:
        s3.upload_file(local_file, bucket, s3_file)
        print("Upload Concluido")
        return True
    except FileNotFoundError:
        print("Arquivo não encontrado")
        return False
    except NoCredentialsError:
        print("credenciais invalidas")
        return False


uploaded = upload_to_aws('Caminho local ex /home/dowload/teste', 'Nome do Bucket', 'caminho do bucket + arquivo')

exit()
