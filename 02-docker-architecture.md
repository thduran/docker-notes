## 1. Componentes Principais

| Componente | Função Principal |
| :--- | :--- |
| **Docker Daemon** | Gerencia objetos (imagens, redes, volumes). Processo principal que executa o trabalho. |
| **Docker CLI** | Interage com o Daemon. |
| **Docker Registry** | Repositório de imagens. |
| **Docker Host** | Onde os componentes são executados. |
| **Docker API** | Interface usada pela CLI comunicação com Daemon. |
| **Docker Engine** | Engloba o Daemon, API e CLI. |

---

## 2. Execução

Atuam sob o Daemon:

* **Containerd:** Gerencia o ciclo de vida completo dos contêineres. Intermedeia Daemon e `runc`. Também gerencia imagens.
* **runc:** Containerd usa para criar e rodas contêineres baseados nas especificações OCI.
* **BuildKit:** Ferramenta de **build** de imagens.

---

## 3. Fluxo

Ciclo de vida de um comando Docker:

1.  **CLI:** Comando é executado (`docker run`).
2.  **API:** O comando é enviado para o Daemon via **API**.
3.  **Daemon:** Recebe a solicitação.
4.  **Containerd:** É instruído pelo Daemon a executar o contêiner.
5.  **runc:** É solicitado pelo containerd para criação do contêiner.
6.  **Container Runtime:** Contêiner é executado.