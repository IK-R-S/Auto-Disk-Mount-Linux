# Como editar o arquivo /etc/fstab e criar uma entrada para montar uma unidade de disco com UUID

### 1. Encontrando o UUID da unidade de disco

O primeiro passo para montar uma unidade de disco usando UUID é encontrar o UUID correto. Você pode fazer isso usando o comando `blkid`. Abra um terminal e digite o seguinte comando:

```
sudo blkid
```

Você verá uma lista de dispositivos de armazenamento conectados ao seu sistema, juntamente com seus UUIDs. Anote o UUID da unidade de disco que você deseja montar.

### 2. Criando um ponto de montagem

Antes de criar uma entrada no arquivo /etc/fstab, é necessário criar um ponto de montagem para a unidade de disco. Para isso, escolha um diretório no seu sistema de arquivos onde deseja montar a unidade de disco. Por exemplo, vamos criar um diretório chamado "disco" dentro da pasta "/media/user/". Para criar o diretório, execute o seguinte comando:

```
sudo mkdir -p /media/user/disco
```

### 3. Editando o arquivo /etc/fstab

Agora é hora de editar o arquivo /etc/fstab e adicionar uma entrada para a unidade de disco. Abra o arquivo /etc/fstab com seu editor de texto preferido:

```
sudo nano /etc/fstab
```

No final do arquivo, adicione uma nova linha com o seguinte formato:

```
UUID=seu_uuid /media/user/disco tipo_de_sistema_de_arquivos defaults 0 1
```
- **exemplo em um HD de 1 Terabyte: `UUID=3vdd121b-r8f-4udhc9-9eqd3il-fe0qwi7uc /media/krs/HD1T ext4 defaults 0 1`**

Substitua "seu_uuid" pelo UUID da unidade de disco que você anotou anteriormente e "tipo_de_sistema_de_arquivos" pelo tipo de sistema de arquivos da unidade de disco (por exemplo, ext4).

Salve as alterações no arquivo e feche o editor de texto.

### 4. Montando a unidade de disco

Finalmente, monte a unidade de disco executando o seguinte comando:

```
sudo mount -a
```

Isso fará com que o sistema de arquivos seja reconfigurado de acordo com as alterações no arquivo /etc/fstab e a unidade de disco seja montada no diretório que você criou.

### 5. Verificando se a unidade de disco foi montada corretamente

Para verificar se a unidade de disco foi montada corretamente, execute o comando `df -h`. Você deve ver a unidade de disco listada com o ponto de montagem que você criou.

Pronto! Agora você tem uma entrada no arquivo /etc/fstab que permite montar automaticamente a unidade de disco com UUID sempre que o sistema é iniciado. Lembre-se de sempre fazer um backup do arquivo antes de editá-lo e de ter conhecimentos avançados em Linux antes de realizar qualquer alteração.
