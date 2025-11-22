# Evo-System - APP

Evo-System é um utilitário de sistema "tudo-em-um" desenvolvido em C# (WPF/.NET Framework). Ele oferece uma interface moderna e elegante para monitoramento de hardware, limpeza de disco, gerenciamento de inicialização e atualização de drivers/softwares.

O projeto foi desenhado com foco em UX moderna (Dark Mode, Glassmorphism) e arquitetura modular, separando a lógica de sistema da interface do usuário.

📋 Funcionalidades Principais
O aplicativo é dividido em módulos acessíveis através de um painel lateral intuitivo:

1. 🏠 Painel Principal (Dashboard)
Monitoramento em Tempo Real: Exibe informações vitais do hardware via WMI (CPU, GPU, RAM e Sistema Operacional).

Scan Inteligente: Um botão de verificação central que analisa o sistema em busca de otimizações, drivers desatualizados e arquivos temporários com feedback visual de progresso.

2. 🧹 Limpeza de Sistema (Cleanup)
Ferramenta robusta para liberar espaço em disco, removendo:

Arquivos Temporários (%TEMP% e AppData).

Cache do Windows e Prefetch.

Cache de Miniaturas (Thumbnails).

Arquivos de Otimização do Windows Update.

Esvaziamento da Lixeira.

3. 🚀 Gerenciador de Inicialização (Startup)
Permite visualizar e gerenciar programas que iniciam junto com o Windows.

Identifica se o programa é de usuário local (HKEY_CURRENT_USER) ou global (HKEY_LOCAL_MACHINE).

Exibe o status (Habilitado/Desabilitado) e o caminho do executável.

4. 📦 Atualizador de Softwares (Winget UI)
Integração nativa com o Windows Package Manager (Winget).

Lista aplicativos instalados que possuem atualizações pendentes.

Exibe versão atual vs. nova versão.

Interface amigável para visualizar as atualizações disponíveis sem precisar usar o terminal.

5. 💾 Drivers e Arquivos Grandes
Drivers: Lista drivers assinados instalados no sistema, exibindo fabricante e versão.

Scanner de Arquivos: Localiza arquivos maiores que 100MB nas pastas do usuário (Documentos, Vídeos, etc.) para ajudar na liberação de espaço.

6. ⚙️ Configurações e Internacionalização
Multi-idioma: Suporte completo a Português (Brasil) e English (US) com troca dinâmica sem reiniciar o app.

Personalização: Opções para iniciar com o Windows e minimizar para a bandeja (Tray).

🛠️ Tecnologias Utilizadas
O projeto está estruturado em uma solução (.sln) contendo três projetos principais:

🖥️ Frontend (EvoSystem.UI)
Framework: WPF (Windows Presentation Foundation) .NET 4.7.2.

Design: Estilização customizada com XAML, uso de ControlTemplate para botões modernos, gradientes e sombras (DropShadow).

Padrões: Code-behind para lógica de UI e Eventos para troca de idioma em tempo real.

🧠 Backend (evosystem-backend)
Tipo: Class Library (.dll).

Core:

System.Management: Para consultas WMI (Hardware e Drivers).

Microsoft.Win32.Registry: Para ler chaves de desinstalação e inicialização.

System.IO: Para manipulação e varredura de arquivos recursiva.

System.Diagnostics.Process: Para comunicação com o CLI do Winget.

🧪 Tester (evosystem-tester)
Aplicação Console para testar as funções do backend isoladamente antes da implementação na UI.

🚀 Como Executar o Projeto
Pré-requisitos
Visual Studio 2022 (ou compatível com suporte a .NET Framework 4.7.2).

Windows 10 ou 11 (Recomendado para suporte completo ao Winget e WMI).

Winget instalado (Padrão no Windows 10/11 atualizado) para a funcionalidade de "Atualizar Apps".

Passo a Passo
Clone o repositório:

Bash

git clone https://github.com/seu-usuario/evo-system.git
Abra o arquivo de solução evosystem-backend.sln no Visual Studio.

Restaure os pacotes NuGet (caso necessário).

Defina o projeto EvoSystem.UI como "Set as Startup Project" (Projeto de Inicialização).

Compile e execute (F5).

⚠️ Nota Importante: Para que funcionalidades como "Limpeza de Disco" (acesso a pastas do sistema) e "Gerenciamento de Drivers" funcionem corretamente, o Visual Studio ou o aplicativo compilado devem ser executados como Administrador.

📂 Estrutura de Pastas
EvoSystem/
├── evosystem-backend/       # Lógica de Negócio (DLL)
│   ├── Actions/             # Lógica de Limpeza (CleanupManager)
│   ├── Core/                # Helpers (WMI, Filesystem)
│   └── Info/                # Classes de Coleta de Dados (SystemInfo, AppManager)
│
├── EvoSystem.UI/            # Interface Gráfica (WPF)
│   ├── Helpers/             # Configurações (AppSettings) e Estado
│   ├── Views/               # Telas (Home, Options, Cleanup, etc.)
│   ├── Resources/           # Estilos e Temas (App.xaml)
│   └── MainWindow.xaml      # Janela Principal
│
└── evosystem-tester/        # App Console para testes
🎨 Galeria de Estilos
O projeto utiliza uma paleta de cores escura e moderna definida em App.xaml:

Fundo Base: #10121a (Quase preto/azul noturno)

Cards: #25283d (Cinza azulado)

Acentos: #3d52fc (Azul Neon) e #00ff88 (Verde status)

Gradientes: Utilizados em botões e fundos para profundidade visual.
