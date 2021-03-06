# PyNFSe

As etapas para o fluxo de trabalho da biblioteca são:

* Configuração do ambiente
* Cadastro de Clientes
* Listar Clientes (opcional)
* Emissão da Nota Fiscal Eletrônica


## Configuração do ambiente

Para a configuração do ambiente (de homologação e/ou produção), é pré-requisito ter um certificado digital válido pelo CNPJ (Cadastro Nacional de Pessoa Jurídica). Este certificado  deve estar cadastrado junto ao portal de emissão de notas da prefeitura de sua cidade.


Ao configurar o ambiente, é necessário ter acesso aos dados listados abaixo.
Para maiores informações,entre em contato o contador responsável pela empresa.


* Número do CNPJ
* Número da inscrição municipal
* Saber se a empresa é ou não optante do Simples Nacional
* Saber se a empresa é ou não incentivador cultural
* Saber se opção principal (default) da empresa for por ter o ISS (Imposto Sobre Serviço) retido na fonte.
* Qual o Regime Especial da empresa:
 * ME Municipal
 * Estimativa
 * Sociedade de profissionais
 * Cooperativa


* Natureza operação padrão ( opções listadas)
 * Tributação no município
 * Tributação fora do município
 * Isenção
 * Imune
 * Exigibilidade suspensa por decisão judicial
 * Exigibilidade suspensa por procedimento administrativo


* Código do Município
* Código de item da lista de serviço padrão
* Código da tributação padrão
* CNAE Padrão
* Alíquota padrão (Em decimal. Por exemplo, 0.02 para 2% de alíquota padrão)

Para configuração dos ambientes,

* Número inicial da RPS ( Recibo Provisório de Serviço )
* Número inicial do lote RPS
* Caminho do certificado
* Senha do certificado

Ao terminar a configuração do ambiente de produção, é recomendado a configuração de um ambiente de homologação.

Dica: Ao configurar os ambientes, quando  informar o caminho para o certificado digital, informe o caminho absoluto.
Por exemplo, se o certificado digital estiver no diretório do usuário padrão (user) no diretório certificado, digite:
```console
/home/user/certificado/certificado_homolog.cert.
```

### Hands-on

No terminal, digite:
```console
$ python pynfse.py configurar_cli
```
Após responder atentamente as perguntas, os seguintes arquivos serão criados:

```console
~/.pynfse/ambiente_homologacao.json
~/.pynfse/ambiente_producao.json
~/.pynfse/clientes.json
~/.pynfse/configuracao.json
~/.pynfse/prestador.json
```

## Cadastro de Clientes

A etapa de cadastrar cliente é importante. Ao emitir a nota fiscal, os dados do cliente precisam ser precisos.

### Hands-on

No terminal, digite:
```console
pynfse cadastrar_tomador
```
## Listar Clientes

Para emissão da NFSe, é importante ter o número do CPF ou do CNPJ do cliente. Esta funcionalidade lista os clientes cadastrados.

### Hands-on

No terminal, digite:
```console
pynfse listar_cliente
```


## Emissão de Nota

Com o ambiente devidamente configurado e os dados do cliente cadastrado, é possível emitir a NFSe. O número do documento solicitado ao rodar esta funcionalidade é o CPF ou CNPJ do cliente. Os demais dados podem ser alterados ou feito uso da configurações padrão, definidos na etapa de configuração do ambiente.

### Hands-on

No terminal, digite:
```console
pynfse emitir_nfse
```
