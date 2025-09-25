# Questões sobre Ferramentas de Monitoramento de Sistema

## 1. Comparação de Finalidade e Acesso
- **Monitor de Atividade (macOS)**: voltado para uso em **desktop**, com interface gráfica intuitiva. Permite inspeção de CPU, memória, disco e rede de forma visual.  
- **`top` (Linux)**: ferramenta em linha de comando, usada via **terminal**. Tem foco em servidores e ambientes sem interface gráfica.  
- **Gerenciador de Tarefas (Windows)**: semelhante ao Monitor de Atividade, com foco em usuários de desktop, oferecendo interface gráfica amigável.  

👉 Diferença principal: **Monitor de Atividade/Gerenciador de Tarefas são gráficos e orientados ao usuário comum; `top` é textual e orientado ao administrador/suporte técnico.**

---

## 2. Monitoramento de CPU
- **Monitor de Atividade (macOS)**: abrir, acessar aba **CPU**, ordenar processos por uso de CPU.  
- **Gerenciador de Tarefas (Windows)**: abrir com `Ctrl+Shift+Esc`, aba **Processos** ou **Detalhes**, ordenar pela coluna **CPU**.  
- **`top` (Linux)**: executar `top` no terminal; os processos aparecem em tempo real, já ordenados por consumo de CPU. Pode usar `Shift+P` para ordenar explicitamente.

---

## 3. Análise de Memória
- **Monitor de Atividade/Gerenciador de Tarefas**: mostram memória física usada, cache, memória comprimida (macOS) e swap.  
- **`top` (Linux)**: exibe:
  - **KiB Mem**: memória física total, usada, livre, buffers.  
  - **KiB Swap**: swap usada e livre.  
  - Por processo: **RES** (memória residente), **VIRT** (virtual), **SHR** (compartilhada).  

👉 Métricas mais relevantes: **RES** (consumo real na RAM) e **%MEM** (percentual de RAM usada pelo processo).

---

## 4. Processos e PIDs
- **PID (Process ID)** identifica de forma única cada processo em execução.  
- Exibição:
  - **Monitor de Atividade**: coluna PID.  
  - **Gerenciador de Tarefas**: aba “Detalhes” mostra o PID.  
  - **`top`**: primeira coluna traz o PID.  

👉 Encerrar processo pelo PID:
- **macOS/Linux**: `kill -9 <PID>`.  
- **Windows**: `taskkill /PID <PID> /F` no Prompt de Comando.

---

## 5. Diferença na Interface
- **Monitor de Atividade**: interface gráfica, organizada em abas (CPU, Memória, Energia, Disco, Rede).  
- **Gerenciador de Tarefas**: interface gráfica com várias guias, mais simples que o Monitor de Atividade.  
- **`top`**: interface **em texto**, interativa pelo terminal.  

👉 Mais visual: **Monitor de Atividade/Gerenciador de Tarefas**.  
👉 Mais orientado a texto: **`top`**.

---

## 6. Monitoramento de Rede
- **Monitor de Atividade**: aba **Rede**, mostra tráfego por processo.  
- **Gerenciador de Tarefas**: aba **Desempenho → Rede**, além de exibir uso por aplicativo.  
- **Linux**: não existe rede no `top` por padrão; usar `iftop`, `nload` ou `netstat -tulpn` para tráfego detalhado.

---

## 7. Análise de Disco
- **Monitor de Atividade**: aba **Disco**, leitura/escrita por processo.  
- **Gerenciador de Tarefas**: aba **Processos** → coluna de disco; aba **Desempenho → Disco** mostra uso geral.  
- **Linux**: `top` não mostra disco diretamente. Ferramentas adicionais:  
  - `iotop` → consumo de I/O por processo.  
  - `iostat` → estatísticas gerais de disco.  

👉 Importância: monitorar gargalos de desempenho, travamentos e processos que abusam de I/O.

---

## 8. Hierarquia de Processos
- **Monitor de Atividade**: não exibe hierarquia de processos (apenas lista simples).  
- **Gerenciador de Tarefas**: mostra processos agrupados por aplicativo, mas não a hierarquia completa de pais/filhos.  
- **Linux**: `top` não mostra hierarquia, mas pode ser combinado com:
  - `pstree` → exibe árvore de processos.  
  - `htop` → versão melhorada do `top`, com hierarquia e cores.

---

## 9. Uso em Servidores vs. Desktops
- **Servidores (sem GUI)**: `top` é mais adequado, pois roda em terminal, consome poucos recursos e funciona em qualquer servidor remoto via SSH.  
- **Desktops (usuários comuns)**: Monitor de Atividade (macOS) e Gerenciador de Tarefas (Windows) são melhores, por fornecerem visualização intuitiva e recursos gráficos.  

👉 Resumindo:  
- **Servidor** → `top` (ou `htop`).  
- **Desktop** → Monitor de Atividade / Gerenciador de Tarefas.

---
