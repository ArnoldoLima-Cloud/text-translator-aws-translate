<p align="center">
  <img src="Amazon Translate.png" alt="Amazon Translate para traduzir textos" width="200"/>
</p>

# Script de Tradução com AWS Translate

Este script utiliza o Amazon Translate para traduzir textos entre diferentes idiomas.

## Pré-requisitos

- Python 3.x
- Biblioteca boto3: `pip install boto3`
- Credenciais AWS configuradas
- Usuário IAM com permissões adequadas
- [Visual Studio Code (VS Code)](https://code.visualstudio.com/) — Editor de código utilizado para desenvolvimento e testes.
- Conta na AWS com permissões para utilizar o serviço [Amazon Translate](https://aws.amazon.com/pt/translate/)

## Configuração de Permissões IAM

### Política IAM Necessária

Para usar o AWS Translate, você precisa criar um usuário IAM com as seguintes permissões:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "translate:TranslateText",
                "translate:GetTerminology",
                "translate:ListTerminologies"
            ],
            "Resource": "*"
        }
    ]
}
```

### Como criar o usuário IAM:

1. **Acesse o Console AWS** → IAM
2. **Usuários** → **Criar usuário**
3. **Nome do usuário:** `translate-user`
4. **Marque:** "Chave de acesso programático"
5. **Próximo: Permissões**
6. **Anexar políticas existentes diretamente**
7. **Criar política** → Cole o JSON acima
8. **Salve as credenciais** (Access Key ID e Secret Access Key)

## Como funciona

### 1. Importação da biblioteca
```python
import boto3
```
- Importa o SDK da AWS para Python
- Permite conectar e usar serviços AWS

### 2. Configuração do cliente Translate
```python
translate = boto3.client(
    'translate',
    region_name='us-east-2',
    aws_access_key_id='AKIAIMR52YLQ7MBA4KIA',
    aws_secret_access_key='CEhdKFK2q5gVm3wy1g2LPTNNfWz6Jc4TebZiQNjj5'
)
```
- Cria conexão com o serviço Amazon Translate
- `region_name`: Define região AWS (Ohio)
- `aws_access_key_id`: Sua chave de acesso
- `aws_secret_access_key`: Sua chave secreta
- Autentica você na AWS

### 3. Tradução do texto
```python
resposta = translate.translate_text(
    Text='Hello, how are you?',
    SourceLanguageCode='en',
    TargetLanguageCode='pt'
)
```
- Chama a API do Translate
- `Text`: Texto a ser traduzido
- `SourceLanguageCode='en'`: Idioma de origem (inglês)
- `TargetLanguageCode='pt'`: Idioma de destino (português)
- Retorna o texto traduzido

### 4. Exibição do resultado
```python
print(resposta['TranslatedText'])
```
- `resposta['TranslatedText']`: Mostra o texto traduzido
- Resultado: "Olá, como você está?"

## Idiomas suportados

- **en**: Inglês
- **pt**: Português
- **es**: Espanhol
- **fr**: Francês
- **de**: Alemão
- **it**: Italiano
- **ja**: Japonês
- **ko**: Coreano
- **zh**: Chinês
- E muitos outros...

## Código Completo

```python
"""
outro tradutor 
"""
import boto3

translate = boto3.client(
    'translate',
    region_name='us-east-2',
    aws_access_key_id='AKIAXZT52YLQ7MBA4KIA',
    aws_secret_access_key='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'
)

resposta = translate.translate_text(
    Text='Hello, how are you?',
    SourceLanguageCode='en',
    TargetLanguageCode='pt'
)

print(resposta['TranslatedText'])
```

## Como executar

```bash
python tradutor.py
```

## Exemplos de uso

### Traduzir do português para inglês:
```python
resposta = translate.translate_text(
    Text='Olá, como você está?',
    SourceLanguageCode='pt',
    TargetLanguageCode='en'
)
```

### Traduzir do inglês para espanhol:
```python
resposta = translate.translate_text(
    Text='Hello, how are you?',
    SourceLanguageCode='en',
    TargetLanguageCode='es'
)
```

## Segurança

⚠️ **Importante**: Nunca compartilhe suas credenciais AWS!

### Alternativa mais segura - Variáveis de ambiente:

```python
import os
import boto3

translate = boto3.client(
    'translate',
    region_name='us-east-2',
    aws_access_key_id=os.getenv('AWS_ACCESS_KEY_ID'),
    aws_secret_access_key=os.getenv('AWS_SECRET_ACCESS_KEY')
)
```

Defina as variáveis no PowerShell:
```bash
$env:AWS_ACCESS_KEY_ID="sua_access_key"
$env:AWS_SECRET_ACCESS_KEY="sua_secret_key"
```

## Observações

O Amazon Translate oferece tradução automática de alta qualidade entre mais de 75 idiomas. O serviço detecta automaticamente o idioma de origem se não especificado e fornece traduções precisas mantendo o contexto do texto original.


---

## 🔗 Saiba mais

Para mais informações sobre o serviço utilizado neste projeto, visite a página oficial do [Amazon Translate](https://aws.amazon.com/pt/translate/).

---

## 📬 Contato e Redes Sociais

Fique à vontade para entrar em contato ou acompanhar meu trabalho nas redes

- 🌐 Site [vempracloud.com.br](httpswww.vempracloud.com.br)
- 💼 LinkedIn [Arnoldo Lima](httpswww.linkedin.cominarnoldolima-arquietocloud)
- 📸 Instagram [@ArnoldoLima.Cloud](httpswww.instagram.comArnoldoLima.Cloud)
- ▶️ YouTube [Arnoldo Lima](httpswww.youtube.com@ArnoldoLima)
