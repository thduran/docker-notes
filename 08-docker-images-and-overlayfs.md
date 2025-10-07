## 1. Imagem vs. Contêiner

Imagem é como a "classe" e o container como o "objeto", na POO.
Nela tem todo o file system pra executar o container.

## 2. Camadas - notas

Cada imagem é feita de **camadas** de somente leitura empilhadas + 1 camada de R/W do container.

Cada instrução no `Dockerfile` é uma nova **camada**.

Camadas não mudam → novas alterações criam novas **camadas**.

Imagens compartilham e reaproveitam **camadas** comuns, economizando espaço.

O container é a imagem base + uma **camada** de R/W criada sobre a imagem base.


## Exemplo visual simples

1.  **Base:** `ubuntu:20.04` (Camada R/O)
2.  **Camada 1:** `apt install curl` (Camada R/O)
3.  **Camada 2:** Copiar arquivos da aplicação (Camada R/O)
4.  **Camada 3:** Expor porta (Camada R/O)
##################################################################
5.  **Contêiner:** Camada temporária de R/W (a única camada modificável)

---

## 3. OverlayFS / Copy-on-Write 

### OverlayFS
* Recurso do Linux que permite empilhar *file systems* de acordo com a necessidade do container.

### Copy-on-Write
* Quando você altera um arquivo da camada base, o Copy-on-Write cria uma cópia modificável na camada de R/W do container.

## 4. Comandos Úteis de Inspeção

Para visualizar a estrutura de camadas na prática:

### Ver camadas de uma imagem e detalhá-las
```bash
docker history nginx
docker inspect nginx
```