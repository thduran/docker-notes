## 1. Contêineres x VMs

Principal diferença: camada de isolamento e consumo de recursos.

| Característica | Máquina Virtual (VM) | Contêiner |
| :--- | :--- | :--- |
| **Isolamento** | Infraestrutura (Hardware) | Processo (Kernel) |
| **Sistema Operacional** | Cada VM tem seu **próprio SO** | **Compartilha** o SO do Host |
| **Intermediação** | **Hipervisor** (Gerencia hardware) | **Motor de Contêiner** (Docker, Containerd etc.) |
| **Consumo de Recurso** | **Alto** (Devido ao SO) | **Baixo** (Apenas o app) |
| **Inicialização** |  **Mais lenta** | **Mais rápida** |

VM: sistema completo e isolado no nível do hardware.
Contêiner: um processo isolado.
Ilustrado em: https://excalidraw.com/#json=7G12O3_suGBDGop-ImCvR,H2YtjBtsDZfi_4rqc1AXwQ

---

## 2. Contêineres - benefícios

Compartilhamento de Kernel traz vantagens no desenvolvimento e implantação:

* **Leveza:** Baixo consumo de recursos e inicialização quase instantânea.
* **Portabilidade:** Executado em qualquer ambiente (local, Azure, AWS, Google Cloud, etc.)
* **Idempotência:** ambiente local **igual** ao de produção, eliminando conflitos de ambiente.
* **Independência de ambientes:** Contêiner empacota só o que precisa, isolando-o do SO.
* **Onboarding facilitado:** Rápida configuração de ambiente complexo para novatos.

---

## 3. Isolamento

Contêineres são processos Linux isolados. Enxergam apenas a si devido a: **namespaces** e **cgroups**.

### Namespaces - "O que você vê"

Responsáveis pelo **isolamento**. Particionam recursos globais do Kernel.

**Isolamento - exemplos**

* Cada contêiner tem sua própria árvore de **processos**, pilha de **rede** e sistema de **arquivos**.

### cgroups - "Quanto você usa"

Eles **limitam recursos**: agrupam processos e aplicam restrições sobre eles garantindo compartilhamento justo de memória/CPU.

**Limitação - exemplos:**

* Contêiner usará no máximo **512MB de memória RAM**.
* Restringir o contêiner a **20% da CPU**.
