# Azure Open AI no VNet - DEV Community

---

## Kenichiro Nakamura  
Publicado em 12 de outubro de 2023  

### Azure Open AI no VNet

GPT models estão hospedados atualmente em vários provedores de serviço, e o Microsoft Azure é um deles.  
Embora os modelos em si sejam os mesmos, existem várias diferenças, incluindo:  
- custo  
- funcionalidades  
- tipo de modelos e versões  
- localização geográfica  
- segurança  
- suporte  
- etc.

Um dos aspectos mais importantes quando usamos isso em um Ambiente Empresarial é, claro, a **segurança**.  
Ao usar os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI **de dentro do VNet**, portanto nenhuma informação circula na rede pública.

---

## Exemplo de Implantação

O repositório de exemplo do Azure fornece arquivos bicep para implantar o Azure Open AI em um ambiente VNet.  
GitHub: [openai-enterprise-iac](https://github.com/Azure-Samples/openai-enterprise-iac)

As principais funcionalidades que o bicep utiliza são:  
- VNet  
- Integração do VNet com Web App  
- Endpoint Privado para Azure Open AI  
- Endpoint Privado para Cognitive Search  
- Zona DNS Privada

Usando essas funcionalidades, todo o tráfego de saída do Web App é roteado **apenas dentro do VNet** e todos os nomes são resolvidos para endereços IP privados. O Open AI e o Cognitive Search desativam o endereço IP público, assim não existe mais endpoint público disponível.

---

## Implantação

O arquivo bicep vai implantar os seguintes recursos no Azure.  
Vamos implantar e confirmar como funciona. Criei um grupo de recursos na região East US para meu teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f ./infra/main.bicep
```

Após rodar o comando acima, vejo que a implantação começou.  
Aguarde até a implantação ser concluída.

---

## Teste

Vamos verificar se a implantação foi bem-sucedida.

### Azure Open AI

Vamos tentar o acesso público primeiro.  
Pude criar uma implantação sem problemas, mas ao tentar pelo Chat playground no meu Portal Azure, recebi o seguinte erro.

Como fica o acesso via Web API?  
Utilizando uma ferramenta avançada do App Service, fiz login na sessão Bash e primeiro fiz um ping para a URL do serviço.  
O endereço IP privado atribuído ao Endpoint Privado foi retornado.  
Em seguida, usei o comando curl para enviar uma requisição para o endpoint.

---

## Comentários Principais  
*(nenhum comentário no momento)*

---

### Sobre o Autor  
Kenichiro Nakamura  
Entrou em 3 de fevereiro de 2018  

---

### Mais de Kenichiro Nakamura  
- Azure ML Prompt flow: Use content safety antes de enviar uma requisição para LLM  
- Não perca tempo escrevendo README, use readme-ai em vez disso  
- C#: Azure Open AI e Function Calling  

---

### Patrocinadores Diamond  
Agradecemos aos nossos patrocinadores Diamond pelo suporte à comunidade DEV:  
- Google AI é o parceiro oficial de modelo e plataforma AI do DEV  
- Neon é o parceiro oficial de banco de dados do DEV  
- Algolia é o parceiro oficial de busca do DEV  

---

## Sobre a DEV Community

Um espaço para discutir e acompanhar o desenvolvimento de software e gerenciar sua carreira na área.   
[Saiba mais](https://dev.to/about)  

---

*Tradução feita para facilitar o acesso aos conteúdos de Azure Open AI em português.*
# Azure Open AI no VNet - DEV Community

---

## Kenichiro Nakamura  
Publicado em 12 de outubro de 2023  

### Azure Open AI no VNet

GPT models estão hospedados atualmente em vários provedores de serviço, e o Microsoft Azure é um deles.  
Embora os modelos em si sejam os mesmos, existem várias diferenças, incluindo:  
- custo  
- funcionalidades  
- tipo de modelos e versões  
- localização geográfica  
- segurança  
- suporte  
- etc.

Um dos aspectos mais importantes quando usamos isso em um Ambiente Empresarial é, claro, a **segurança**.  
Ao usar os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI **de dentro do VNet**, portanto nenhuma informação circula na rede pública.

---

## Exemplo de Implantação

O repositório de exemplo do Azure fornece arquivos bicep para implantar o Azure Open AI em um ambiente VNet.  
GitHub: [openai-enterprise-iac](https://github.com/Azure-Samples/openai-enterprise-iac)

As principais funcionalidades que o bicep utiliza são:  
- VNet  
- Integração do VNet com Web App  
- Endpoint Privado para Azure Open AI  
- Endpoint Privado para Cognitive Search  
- Zona DNS Privada

Usando essas funcionalidades, todo o tráfego de saída do Web App é roteado **apenas dentro do VNet** e todos os nomes são resolvidos para endereços IP privados. O Open AI e o Cognitive Search desativam o endereço IP público, assim não existe mais endpoint público disponível.

---

## Implantação

O arquivo bicep vai implantar os seguintes recursos no Azure.  
Vamos implantar e confirmar como funciona. Criei um grupo de recursos na região East US para meu teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f ./infra/main.bicep
```

Após rodar o comando acima, vejo que a implantação começou.  
Aguarde até a implantação ser concluída.

---

## Teste

Vamos verificar se a implantação foi bem-sucedida.

### Azure Open AI

Vamos tentar o acesso público primeiro.  
Pude criar uma implantação sem problemas, mas ao tentar pelo Chat playground no meu Portal Azure, recebi o seguinte erro.

Como fica o acesso via Web API?  
Utilizando uma ferramenta avançada do App Service, fiz login na sessão Bash e primeiro fiz um ping para a URL do serviço.  
O endereço IP privado atribuído ao Endpoint Privado foi retornado.  
Em seguida, usei o comando curl para enviar uma requisição para o endpoint.

---

## Comentários Principais  
*(nenhum comentário no momento)*

---

### Sobre o Autor  
Kenichiro Nakamura  
Entrou em 3 de fevereiro de 2018  

---

### Mais de Kenichiro Nakamura  
- Azure ML Prompt flow: Use content safety antes de enviar uma requisição para LLM  
- Não perca tempo escrevendo README, use readme-ai em vez disso  
- C#: Azure Open AI e Function Calling  

---

### Patrocinadores Diamond  
Agradecemos aos nossos patrocinadores Diamond pelo suporte à comunidade DEV:  
- Google AI é o parceiro oficial de modelo e plataforma AI do DEV  
- Neon é o parceiro oficial de banco de dados do DEV  
- Algolia é o parceiro oficial de busca do DEV  

---

## Sobre a DEV Community

Um espaço para discutir e acompanhar o desenvolvimento de software e gerenciar sua carreira na área.   
[Saiba mais](https://dev.to/about)  

---

*Tradução feita para facilitar o acesso aos conteúdos de Azure Open AI em português.*
