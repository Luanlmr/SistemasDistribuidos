## 1. Análise Comparativa

### Carro.java (Semáforo)
* **Mecanismo:** Utiliza a classe `java.util.concurrent.Semaphore`.
* **Configuração:** O semáforo foi iniciado com **10 permissões** (`new Semaphore(10)`).
* **Comportamento:** O programa permite que até **10 threads (carros)** acessem a região crítica (estacionamento) simultaneamente.
* **Resultado Prático:** Como foram lançadas 20 threads, as primeiras 10 entram quase instantaneamente. A 11ª thread só consegue entrar quando uma das 10 primeiras libera a vaga (`release`). Isso simula perfeitamente um **recurso compartilhado com capacidade limitada** (ex: um estacionamento com vagas múltiplas).

### CarroLock.java (Lock)
* **Mecanismo:** Utiliza a interface `java.util.concurrent.locks.Lock` (implementação `ReentrantLock`).
* **Configuração:** O Lock funciona como um bloqueio de exclusão mútua.
* **Comportamento:** O objetivo do Lock é garantir que **apenas uma thread** acesse o recurso por vez.
* **Resultado Prático:** Ao contrário do Semáforo, o Lock não permite acesso simultâneo. Ele cria uma fila onde um carro deve sair totalmente para o próximo entrar. Isso simula um **recurso único** ou uma seção crítica que não pode sofrer interferência (ex: uma ponte de via única ou gravação em um arquivo).

