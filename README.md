# Python-Challenge

## _Features_
1.  Criar um report de budget da sua conta AWS utilizando Python
      -  Criar uma Lambda;
      -  Converter a saida para csv;
      -  Salvar relatório no S3
      -  Criar o alerta de budget utilizando boto na sua conta aws para enviar o alerta quando chegar no valor estipulado por vocês

2.  Criar um monitoramento no personal health da aws
      -  Criar uma lambda
      -  Converte a saida para um csv
      -  Salvar  saida no S3

3.  Criar um lambda de monitoramento de recursos que não possui tags
      -  Criar uma lambda
      -  Varrer a conta uma vez ao dia
      -  criar tag no recurso
      -  Gravar no S3 em arquivo de log, qual recurso foi marcado a tag e hora e dia

4.  Criar um lambda que leia os recursos no S3 anteriores normalize os dados e jogue no dynamodb
      -  Criar uma lambda
      -  ler os arquivos do S3
      -  normalizar os arquivos (Colocando os campos vazio como null)
      -  jogar os conteudos  por tabelas separadas no dynamodb

## :wrench: <span style="color:black"><b> Implementação do código: </b> </span>    

1. **Faça fork do [repositório](https://github.com/Furipe09/Desafio-2.git)**

2. **Baixe o código para o seu "vscode", conforme exemplo abaixo:**
   
   *Utilize o repositório do seu GIT*
    ```sh
    git clone https://github.com/Furipe09/Desafio-2.git
    ```
    
3.  **Crie seu Bucket S3 que servirá de respositório para o tfstate.**
    - 3.1 *Entre na pasta 'remote-state'*
    ```sh
    cd ...Desafio-2/remote-state
    ```
    - 3.2 *Inicializando o ambiente*
    ```sh
    terraform init
    ```
    - 3.3  Montando o plano de criação do Bucket S3
    ```sh
    terraform plan
    ```
    - 3.4 Aplicando a criação do Bucket S3 com auto-aprove
    ```sh
    terraform apply -auto-approve
    ```
    
4.  **Após a criação do bucket S3, pegue na AWS o nome gerado para utilizar de parametro na alteração do arquivo /Infra/variables.tf.** 
  Exemplo:

    ```sh
    variable "bucket_tfstate" {
    type    = string
    default = "tfstate-2-831989750918-terraform"
    } 
    ```
5. **Altere o caminho da sua chave pública  que servirá de modelo para criação do key_pair das EC2.** 
   - *No arquivo /Infra/variables.tf*
   - *Caso não tenha chave pública, [aqui](https://www.spiritsec.com/2019/06/04/como-gerar-e-usar-chaves-ssh-no-linux/) tem um exemplo de como cria-la*
    ```sh
    variable "aws_modelo_chave_publica" {
    type    = string
    default = "/home/furion/.ssh/id_rsa.pub"
    }
    ```
6. **Altere com o valor da sua profile da aws no arquivo /Infra/variables.tf.** 
   
    ```sh
    variable "aws_profile" {
    type    = string
    default = "tf009"
    }
    ```

7. **As demais variaveis contidas no /Infra/variables podem ser alteradas, porém cada uma tem uma explicação de qual impacto isso acarretará. Para inicio, não é necessário alterar nenhuma outra váriavel.**     


## :rocket: <span style="color:black"><b> Subindo a Infra na AWS </b> </span>    


1.  **Execute a criação dos recursos na pasta '/Infra/'**
    - 1.1 Inicializando o ambiente

    ```sh
    terraform init
    ```
    - 1.2  Montando o plano de criação dos recursos
    ```sh
    terraform plan
    ```
    - 1.3 Aplicando a criação dos recursos com auto-aprove
    ```sh
    terraform apply -auto-approve
    ```
2. :bomb: **Por fim, não esquecer de destruir o ambiente, primeiro na pasta '2-Infra/' e depois na pasta '1-remote-state/'**
    ```sh
    terraform destroy
    ```
# **References**
  - https://docs.aws.amazon.com/lambda/latest/dg/lambda-samples.html
  - https://github.com/awsdocs/aws-lambda-developer-guide/tree/main/sample-apps/blank-python
  - https://towardsdatascience.com/lambda-functions-with-practical-examples-in-python-45934f3653a8
  - https://itau.udemy.com/course/python-scripts-para-automacao-amazon-aws/learn/lecture/22421268#overview
