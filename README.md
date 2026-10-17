Próxima geração do pacote de driver e biblioteca input32

InpOutNG é uma DLL e um driver de código aberto para Windows que permite acesso direto a portas de hardware (como as portas paralela e serial) a partir de programas de usuário. Foi originalmente desenvolvido pela equipe da Logix4U para Windows 9x e versões de 32 bits do NT (NT/2000/XP/2003 etc.). Posteriormente, o trabalho foi continuado por Philip Gibbons e ficou conhecido como inpout32. Desde 2021, o desenvolvimento do projeto continua aqui e novos recursos foram introduzidos.

Além disso, hoje em dia é fácil comprar hardware novo com Intel® Core™ i7 integrado, instalá-lo em um backplane PICMG 1.0 com 14 slots ISA, instalar o Windows 10 e se divertir... ou realizar algumas tarefas industriais... Um barramento de quase 40 anos, considerado obsoleto para daqui a 30 anos, ainda está vivo...

Requisitos
Windows 32 ou 64 bits (testado no Windows 7 e 10)
Modo de teste ou teste de assinatura de driver desativado devido às políticas de segurança da Microsoft.
Direitos de administrador, necessários apenas para o procedimento de instalação do driver.
Recursos
Acesso às portas de E/S de hardware ISA/PCI
Processamento de tarefas - múltiplas solicitações de E/S podem ser executadas em lote com uma única chamada de função.
Tratamento de IRQ - você pode atribuir uma IRQ de hardware a um driver, como era feito originalmente no Windows 95/98, e instruir uma DLL a notificá-lo sobre a ocorrência de uma IRQ ou executar alguma tarefa adicional nesse caso.
Instalação do InpOutNG:
Para usuários finais:
Sim, a nova versão tem o mesmo nome de DLL inpout32.dll. Isso foi feito intencionalmente para garantir a compatibilidade com qualquer software que utilize a biblioteca original de Phil Gibbons.

Se você já possui um aplicativo que utiliza inpout32.dlleste programa, basta colocar minha versão inpout32.dllna mesma pasta que o programa original. Normalmente, essa pasta é a mesma do arquivo executável do aplicativo. Esta versão pode ser instalada e executada em sistemas operacionais de 32 e 64 bits, mas na primeira execução, em sistemas operacionais Vista e posteriores, é necessário executá-la como administrador.

O arquivo binário baixado inclui um pequeno InstallDriver.exeprograma para fazer isso por você. Ele foi compilado com a opção «require Administrator» (exigir privilégios de administrador).

No gerenciador de dispositivos do Windows, você pode configurar o dispositivo do sistema para IntOutNG e definir uma IRQ que o driver irá escutar. Assim, seu aplicativo poderá usar waitForIrqfunções doOnIrqsemelhantes às que já estão WaitForSingleObjectem uso.

Para desenvolvedores:
Os arquivos de driver estão incluídos como um recurso na DLL. Tudo o que você precisa fazer é vincular a DLL apropriada em seu programa e deverá funcionar.

NOTA: Quando a DLL é carregada pela primeira vez, o driver apropriado é instalado e utilizado. Uma janela de console com saída de texto será exibida; isso é normal.

NOTA: No Vista e versões posteriores, são necessárias permissões elevadas para instalar o driver.

Recomendo usar a vinculação em tempo de execução à interface C (carregando a biblioteca manualmente) em C++, de forma semelhante ao funcionamento das chamadas de interoperabilidade do .NET. No entanto, você também pode usar os arquivos .LIB e de cabeçalho fornecidos para vincular em tempo de compilação, se isso for mais adequado para sua aplicação.

Desenvolvimento:
Existem exemplos e algumas instruções de uso na samplespasta.

Lembre-se de que, em sistemas operacionais de 64 bits, muitos aplicativos ainda são, e até mesmo agora em 2021 são, de 32 bits.

Esperamos que alguma documentação apareça na pasta de documentos...

DOAÇÕES
Se você quiser aumentar minha motivação para continuar o desenvolvimento, pode fazer uma doação. O valor não importa, é apenas um sinal para mim de que o tempo que dediquei a este projeto está ajudando alguém. Além disso, preciso de comida para o meu urso, isso o acalma e não atrapalha meu hobby de desenvolvimento.

DOAR
