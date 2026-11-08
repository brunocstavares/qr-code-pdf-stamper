# 📄 Carimbador SEI - IPHAN

Uma ferramenta web leve, de arquivo único (Single-file) e 100% executada no navegador (Client-Side) desenvolvida para inserir carimbos digitais de aprovação em pranchas de projetos arquitetônicos. O sistema foi projetado especificamente para atender fluxos de trabalho onde há restrições de segurança em servidores locais (ausência de PHP/Node no backend) na preparação de arquivos em lote para o Sistema Eletrônico de Informações (SEI).

---

## ✨ Funcionalidades Principais

*   **100% Client-Side:** Todo o processamento (leitura, edição, geração de imagem e salvamento do PDF) ocorre localmente na memória do navegador do usuário. Nenhum documento sigiloso é enviado para a internet.
*   **Posicionamento Visual Intuitivo:** Interface "Drag and Drop" (arrastar e soltar) que permite posicionar o selo visualmente sobre a prancha do projeto.
*   **Paginação Independente e Inteligente:** 
    *   Permite posicionar o carimbo em locais diferentes para cada página do PDF.
    *   Caso as pranchas tenham o selo no mesmo local, basta posicionar na Página 1 e o sistema replicará a posição para as demais automaticamente.
*   **Correção Nativa de Rotação (Pranchas Deitadas):** O motor lê metadados internos de PDFs rotacionados em CAD/BIM e aplica contra-rotações matemáticas para garantir que o carimbo fique sempre alinhado e "em pé".
*   **QR-Code Dinâmico Integrado:** Gera o código bidimensional instantaneamente com base no Parecer Técnico, Processo Administrativo e Nº SEI.
*   **Feedback Visual Condicional:** O texto do laudo muda de cor automaticamente de acordo com o resultado (Verde para Aprovado, Vermelho para Reprovado).
*   **Validação de Dados:** Impede a geração de arquivos com informações obrigatórias em branco.

---

## 🚀 Como Utilizar (Passo a Passo)

1.  **Abrir a Ferramenta:** Dê um duplo-clique no arquivo `carimbador.html` para abri-lo em seu navegador padrão (Google Chrome, Microsoft Edge, Firefox). *Requer conexão com a internet apenas no momento de abrir, para carregar as bibliotecas visuais*.
2.  **Preencher Metadados:** Na barra lateral esquerda, preencha todos os campos obrigatórios marcados com asterisco `*` (Nº do processo, Parecer, SEI e Resultado).
3.  **Carregar o PDF:** Clique em `Escolher arquivo` e selecione a planta arquitetônica em formato PDF (apenas 1 arquivo por vez).
4.  **Posicionar o Carimbo:** 
    *   Aguarde o carregamento visual da prancha.
    *   Clique e arraste a **caixa vermelha tracejada** para o local exato onde o carimbo deve ser fixado (geralmente sobre o selo da prancha).
5.  **Ajustar Paginação (Opcional):** Se o seu PDF tiver várias páginas e o selo mudar de lugar em alguma delas, use os botões `« Anterior` e `Próxima »` e posicione a caixa vermelha especificamente naquela folha.
6.  **Gerar e Baixar:** Clique no botão azul `Carimbar e Baixar PDF`. O sistema fará o processamento e o download iniciará automaticamente, adicionando o sufixo `_carimbado` ao nome original do arquivo.

---

## 🛠️ Detalhes Técnicos e Dependências

A ferramenta contorna firewalls corporativos utilizando CDNs (Content Delivery Networks) liberadas universalmente (`cdnjs`). Nenhuma instalação local no sistema operacional é necessária.

**Bibliotecas Utilizadas:**
*   [pdf.js (Mozilla)](https://mozilla.github.io/pdf.js/): Motor de renderização visual. Transforma a página do PDF em uma imagem dentro do `<canvas>` HTML para visualização do usuário.
*   [pdf-lib](https://pdf-lib.js.org/): Biblioteca robusta de manipulação de PDF em JavaScript puro. Utilizada para fundir a imagem do QR Code, os textos e salvar o novo documento sem corromper as camadas originais do CAD.
*   [node-qrcode](https://github.com/soldair/node-qrcode): Utilizada via browser build para converter o texto estruturado do parecer em uma matriz de imagem Base64.

---

## 📜 Histórico de Versões (SemVer)

| Versão  | Data       | Principais Alterações |
| :---    | :---       | :--- |
| **v1.0.1** | 07/11/2026 | Inclusão de controle SemVer. Adição de modal de histórico de versões (Changelog visual) no rodapé do aplicativo. Layout flexível da sidebar ajustado. |
| **v1.0.0** | 07/11/2026 | **Baseline Estável.** Validação de campos obrigatórios; Paginação independente; Lógica de contra-rotação ativada (correção de folhas paisagem disfarçadas); Texto colorido (Verde/Vermelho) conforme aprovação. |

---

*Desenvolvido para otimizar a rotina de análise técnica e integração de pareceres espaciais com o SEI.*
