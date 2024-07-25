# Computação paralela
---
## Programa vs Processo
---
- **Programa**: uma sequência de instruções escritas em uma linguagem de programação e normalmente armazenadas num arquivo

- **Processo**: uma instância de um programa que está sendo executado pelo computador 
---
![[Process.jpg]]

---
- Situações há em que é útil reordenar e agrupar as instruções para que sejam **executadas em paralelo** sem mudar o resultado do programa.
- O paralelismo traz desafios relevantes
---
## Sincronização
- Vital para garantir a inalterância do resultado e prevenir efeitos indesejados
---
### Técnicas comuns
- **Locks**
- **Monitors**
- **Semáforos**: sinalizadores que controlam o acesso a recursos compartilhados
- **Operações atômicas**: conjuto de operações tomadas como átomos, i. e, outros processos não devem poder dividir a sua execução antes que ela mesma tenha sido completamente executada
---
## Tipos de paralelismo
- no mesmo computador $\rightarrow$ **programação concorrente**
- em computadores distintos $\rightarrow$ **sistemas distribuídos**
---

## Programação concorrente
---
### Definição
- **Concorrência**: a execução simultânea de múltiplas tarefas *por um mesmo dispositivo*

- **Características:**
	- Beneficia-se de processadores *multicore* ou de computadores *multiprocessador*
	- É comum o uso de memória compartilhada entre as CPU para melhor comunicação
---
### Modelos e técnicas:
- Baseado em dados
- Baseado em processo
- Baseado em thread
---
### Baseado em dados
- *Operações semelhantes* aplicadas em partições *distintas* do conjunto de dados
	- Grandes volumes de dados 
	- O resultado de uma operação não afeta o das demais
---
### Baseado em thread
- **Thread:** uma sequência de instruções que podem ser executadas independentemente *dentro de um processo*
- **Em Python**:  ```import threading```
---
#### Vantagens
- Melhor desempenho para operação de IO: a CPU não fica obstruida enquanto espera uma requisição
	- Ler e gravar dados em um arquivo.
	- Imprimir os resultados de um programa na tela.
	- Conectar-se a um banco de dados e trocar informações.
	- Enviar dados pela rede
	- Ler e gravar dados de um dispositivo de armazenamento externo
	- Interagir com o sistema operacional para realizar operações.
---
#### Desvantagem
- Ineficientes para programas que executam tarefas intensivas de CPU.
	- A implementação de Python não lida bem com multithreading 
	- Python GIL dificulta para evitar a corrupção dos dados na memória 
---
### Baseado em processo
- Execução simultanea de diferentes *tasks* em distintas unidades de processamento
- **Em Python**: ```import multiprocessing```
---
#### Vantagens
- Permite criar processos separados, cada um com seu interpretador e GIL individual
- Otimiza tarefas que envolve muitos cálculos, sem muita espera por IO (tarefas CPU-bound)
- Melhor proveito dos múltiplos núcleos do processador
- ---
## Sistemas distribuídos
---
- **Distribuição** conecta multiplos computadores numa rede em torno de uma tarefa comum
- Destaques:
	- Computadores independentes
	- Nós podem estar espalhados ao redor do globo
---
- Comunicação entre nós normalmente via **message-passing** (deve ser eficiente) 
- Balanceamento da carga de trabalho 
---
### Arquiteturas principais
---
#### Cliente-server
- Computador central orquestra os periféricos, provendo os recursos e os serviços necessários
%% ![[images.png]] %%
---
#### Peer-to-peer
- Computadores *colaboram* sem uma autoridade central, envolvendo a comunicação e o compartilhamento de recursos
---
![[client-server-vs-p2p.png]]

---
### Modelo principal: MPI
---
- **Message-passing:** modelo no qual os dados são movidos do espaço de endereço de um processo para o de outro processo através de operações cooperativas em cada processo.
- [**MPI**](https://www.mpi-forum.org/docs/mpi-2.2/mpi22-report.pdf) é uma especificação para uma interface padronizada de message-passing
---
#### Vantagens (1/2)
- Oferece uma **interface consistente** para diversas arquiteturas de computação paralela, especialmente a de **memória distribuida**
- Usada em aplicações científicas e de engenharia relacionadas a modelagem, **simulação**, design e processamento de sinal
---
#### Vantagens (2/2)
- **Portabilidade** entre sistemas operacionais
- Fornece **operações básica de comunicação** ponto-a-ponto e coletivas, gerenciamento de processos, datatypes (...) (!!)
---
#### Considerações finais
- Mesmas dificuldades da concorrência em relação ao sincronismo dos resultados
- As mensagens são transferidas entre processos de forma **síncrona**, exigindo um reconhecimento, ou de forma **assíncrona**.
---
# Referências
- [Computação paralela](https://pt.wikipedia.org/wiki/Computa%C3%A7%C3%A3o_paralela#:~:text=Paralelismo%20em%20tarefa%20%C3%A9%20a,em%20diferentes%20conjuntos%20de%20dados)
- [Acelerando o Python: Um Guia Prático para Paralelismo, Concorrência e Clusters](https://www.linkedin.com/pulse/acelerando-o-python-um-guia-pr%C3%A1tico-para-paralelismo-e-faig/)
- [Aprenda sobre Concorrência e Paralelismo em Python](https://pythonacademy.com.br/blog/aprenda-sobre-concorrencia-e-paralelismo-em-python)
- [Message Passing Interface — MPI](https://mpi4py.readthedocs.io/en/stable/overview.html#support-for-gpu-aware-mpi)
- [Distributed Programming](https://www.studysmarter.co.uk/explanations/computer-science/computer-programming/distributed-programming/)
- [MPI Specification](https://www.mpi-forum.org/docs/mpi-2.2/mpi22-report.pdf)