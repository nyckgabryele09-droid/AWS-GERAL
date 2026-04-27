# Laboratório 3: Introdução ao Amazon EC2
Visão geral e objetivos do laboratório
diagrama de arquitetura
Este laboratório oferece uma visão geral básica sobre como iniciar, redimensionar, gerenciar e monitorar uma instância do Amazon EC2.

O Amazon Elastic Compute Cloud (Amazon EC2) é um serviço da web que fornece capacidade computacional redimensionável na nuvem. Ele foi projetado para facilitar a computação em nuvem na escala da web para os desenvolvedores.

A interface de serviço da web simples do Amazon EC2 permite que você obtenha e configure capacidade com o mínimo de esforço. Ela oferece um controle completo de seus recursos de computação e permite a execução no ambiente de computação comprovado da Amazon. O Amazon EC2 reduz o tempo necessário para obter e inicializar novas instâncias do servidor em minutos, permitindo o rápido escalonamento da capacidade para mais ou para menos, de acordo com a evolução dos requisitos de computação.

O Amazon EC2 altera a economia da computação, permitindo que você pague somente pela capacidade que realmente utiliza. O Amazon EC2 oferece aos desenvolvedores as ferramentas para criar aplicativos resistentes a falhas e isolá-los de situações de falha comuns.

Depois de concluir o laboratório, você será capaz de:

Iniciar um servidor web com proteção contra encerramento ativada.
Monitorar sua instância do EC2.
Modificar o grupo de segurança que seu servidor web está usando para permitir acesso HTTP.
Redimensionar sua instância do Amazon EC2 de acordo com a necessidade e ativar a proteção contra interrupção.
Explorar os limites do EC2.
Testar a proteção contra interrupção.
Interromper a instância do EC2.
 
Duração
O laboratório levará aproximadamente 35 minutos para ser concluído.

Restrições de serviço da AWS
Neste ambiente de laboratório, o acesso aos serviços e às ações de serviços da AWS pode ser restrito aos necessários para concluir as instruções do laboratório. Você poderá encontrar erros se tentar acessar outros serviços ou executar ações além das descritas neste laboratório.

Acessar o Console de Gerenciamento da AWS
No topo destas instruções, escolha  Iniciar laboratório.

A sessão de laboratório será iniciada.

Um cronômetro ficará visível no topo da página e mostrará o tempo restante da sessão.

 Dica: para atualizar a duração da sessão a qualquer momento, selecione  Iniciar laboratório novamente antes que o cronômetro seja zerado.

Antes de continuar, aguarde até o ícone circular à direita do link da AWS  no canto superior esquerdo ficar verde. 

Para se conectar ao Console de Gerenciamento da AWS, escolha o link da AWS no canto superior esquerdo.

Uma nova guia do navegador será aberta, e você acessará o console.

 Dica: se uma nova guia não for aberta, você verá um banner ou um ícone no topo do navegador com uma mensagem informando que o programa está impedindo que o site abra janelas pop-up. Selecione o banner ou ícone e escolha Permitir pop-ups.

Organize a guia do Console de Gerenciamento da AWS para que ela seja exibida com essas instruções. O ideal seria você poder visualizar as duas guias do navegador ao mesmo tempo para facilitar o acompanhamento das etapas do laboratório.

Como obter crédito para seu trabalho
Ao final deste laboratório, você receberá instruções de como enviar o laboratório para receber uma pontuação com base em seu progresso.

 Dica: o script que verifica seu trabalho só pode conceder pontos se você nomear recursos e definir as configurações conforme especificado. Em particular, os valores nessas instruções que aparecem This Format devem ser inseridos exatamente como documentado (diferenciando letras maiúsculas de minúsculas).

Tarefa 1: Iniciar a instância do Amazon EC2
Nesta tarefa, você executará uma instância do Amazon EC2 com proteção contra encerramento e a proteção contra interrupção. A proteção contra encerramento evita que você encerre sem querer a instância do EC2 e a proteção contra interrupção evita que você interrompa sem querer a instância do EC2. Você também especificará um script de Dados do usuário ao iniciar a instância que implantará um servidor web simples.

No Console de Gerenciamento da AWS, selecione o menu  Serviços, selecione Computação e depois EC2.

Observação: Verifique se seu console do EC2 está gerenciando recursos na região Norte da Virgínia (us-east-1).  É possível verificar isso no menu suspenso na parte superior da tela, à esquerda do nome de usuário. Se o menu não indicar “Norte da Virgínia”, selecione a região Norte da Virgínia no menu de regiões antes de prosseguir para a próxima etapa.

Selecione o menu Executar instância  e Executar instância.

Etapa 1: Nome e tags
Dê à instância o nome Web Server.

 O nome dado à instância será armazenado como uma tag. As tags permitem categorizar os recursos da AWS de várias maneiras, por exemplo: por finalidade, proprietário ou ambiente. Isso é útil quando há muitos recursos do mesmo tipo — você pode identificar rapidamente um recurso específico com base nas tags atribuídas. Cada tag tem uma chave e um valor, ambos definidos por você. Você pode definir várias tags para associá-las com a instância, se desejar.

Nesse caso, a tag a ser criada consistirá em uma chave chamada Name com o valor de Web Server.

Etapa 2: Imagens do aplicativo e SO (imagem de máquina da Amazon)
Na lista de AMIs Quick Start disponíveis, mantenha a AMI padrão do Amazon Linux selecionada. 

Também mantenha a configuração padrão Amazon Linux 2023 AMI.

 Uma imagem de máquina da Amazon (AMI) contém as informações necessárias para iniciar uma instância, que é um servidor virtual na nuvem. Uma AMI inclui:

Um modelo para o volume raiz da instância (por exemplo, um sistema operacional ou um servidor de aplicativos com aplicativos)
Permissões de execução que controlam quais contas AWS podem usar a AMI para iniciar instâncias
Um mapeamento de dispositivos de blocos que especifica quais volumes devem ser anexados à instância quando ela for executada
A lista Quick Start contém as AMIs mais usadas. Você também pode criar sua própria AMI ou selecionar uma AMI no AWS Marketplace, uma loja on-line na qual você pode vender ou comprar software executado na AWS.

Etapa 3: Tipo de instância
No painel Tipo de instância, mantenha o padrão t2.micro selecionado.

 O Amazon EC2 fornece uma ampla seleção de tipos de instâncias otimizados para se adequarem a diferentes casos de uso. Os tipos de instâncias consistem em várias combinações de CPU, memória, armazenamento e capacidade de redes, oferecendo flexibilidade de escolha da composição adequada de recursos para os seus aplicativos. Cada tipo de instância inclui um ou mais tamanhos de instância, permitindo que você dimensione seus recursos conforme os requisitos da carga de trabalho de destino.

O tipo de instância t2.micro tem 1 CPU virtual e 1 GiB de memória. 

Observação: talvez você não possa usar outros tipos de instância neste laboratório.

Etapa 4: Par de chaves (login)
Para o Nome do par de chaves: obrigatório, selecione vockey. 

 O Amazon EC2 usa criptografia de chave pública para criptografar e descriptografar as informações de login. Para garantir que você conseguirá acessar o SO convidado da instância criada, identifique um par de chaves existente ou crie um par de chaves ao executar a instância. Em seguida, o Amazon EC2 instalará a chave no SO convidado quando a instância for executada.  Dessa forma, quando você tentar fazer login na instância e fornecer a chave privada, terá autorização para se conectar à instância.

Observação: neste laboratório, você não usará o par de chaves especificado ao acessar a instância.

 

Etapa 5: Configurações de rede
Ao lado de Configurações de rede, selecione Editar.

 

Para VPC, selecione Lab VPC.

A VPC do laboratório foi criada com base em um modelo do AWS CloudFormation durante o processo de configuração do seu laboratório. Essa VPC inclui duas sub-redes públicas em duas Zonas de Disponibilidade diferentes.

 Observação: mantenha a sub-rede padrão PublicSubnet1. Essa é a sub-rede na qual a instância será executada. Observe que, por padrão, a instância receberá um endereço IP público.

 

Em Firewall (grupos de segurança), selecione  Criar grupo de segurança e configure:

Nome do grupo de segurança: Web Server security group

Descrição: Security group for my web server

 Um grupo de segurança atua como um firewall virtual que controla o tráfego de uma ou mais instâncias. Ao executar uma instância, você pode associar um ou mais grupos de segurança a ela. Você adiciona regras a cada grupo de segurança que permitem o tráfego de entrada ou de saída das instâncias associadas. É possível modificar as regras de um grupo de segurança a qualquer momento. As novas regras são aplicadas automaticamente a todas as instâncias associadas ao grupo de segurança.

Em Regras dos grupos de segurança de entrada, observe que existe uma regra. Remova essa regra.

 

Etapa 6: Configurar o armazenamento
Na seção Configurar armazenamento, mantenha as configurações padrão.

 O Amazon EC2 armazena dados em um disco virtual anexado à rede chamado Elastic Block Store.

Você executará a instância do Amazon EC2 usando um volume de disco padrão de 8 GiB. Esse será o volume-raiz, também conhecido como volume de inicialização.

 

Etapa 7: Detalhes avançados
Expanda  Detalhes avançados.

 

Em Proteção contra encerramento, selecione Ativar.

 Quando uma instância do Amazon EC2 não for mais necessária, ela poderá ser terminada, ou seja, a instância será excluída e os recursos serão liberados. Uma instância encerrada não pode ser acessada novamente, e os dados nela não podem ser recuperados. Se quiser evitar que a instância seja encerrada acidentalmente, ative a proteção contra encerramento para a instância, o que impede que ela seja encerrada enquanto a configuração permanecer ativada.

 

Role até a parte inferior da página e copie e cole o código mostrado abaixo na caixa Dados do usuário:

#!/bin/bash
dnf install -y httpd
systemctl enable httpd
systemctl start httpd
echo '<html><h1>Hello From Your Web Server!</h1></html>' > /var/www/html/index.html
 Ao executar uma instância, você pode passar os dados do usuário a ela, que podem ser usados para realizar tarefas automatizadas de instalação e configuração após a inicialização da instância.

A instância está executando o Amazon Linux 2023. O script de shell que você especificou será executado como o usuário raiz do SO convidado quando a instância for iniciada. O script:

Instalará um servidor web Apache (httpd).
Configurará o servidor web para ser iniciado automaticamente na inicialização.
Executará o servidor web quando a instalação for concluída.
Criará uma página da web simples.
 

Etapa 8: Executar a instância
Na parte inferior do painel Resumo, selecione Executar instância.

Uma mensagem de sucesso será exibida.

 

Selecione Visualizar todas as instâncias.

Na lista de instâncias, selecione  Web Server. 

Verifique as informações exibidas na guia Detalhes. Ela inclui informações sobre o tipo de instância, as configurações de segurança e de rede.

A instância é atribuída a um DNS IPv4 público, que você pode usar para contatar a instância pela internet.

 Para visualizar mais informações, arraste o divisor da janela para cima.

Inicialmente, a instância aparecerá em um estado Pendente, o que significa que ela está sendo inicializada. Depois, ela mudará para Inicializando e, por fim, para Em execução.

 

Aguarde até que a instância exiba o seguinte:

Estado da instância:  Em execução
Verificações de status:   2/2 verificações aprovadas
 

 Parabéns! Você executou com sucesso sua primeira instância do Amazon EC2.

 

Tarefa 2: Monitorar a instância
O monitoramento é uma parte importante da manutenção da confiabilidade, disponibilidade e desempenho das instâncias do Amazon Elastic Compute Cloud (Amazon EC2) e das soluções da AWS.

 

Escolha a guia Verificações de status.

 Com o monitoramento de status de instâncias, você pode determinar rapidamente se o Amazon EC2 detectou problemas que podem impedir as instâncias de executar aplicações. O Amazon EC2 realiza verificações automáticas em cada instância do EC2 em execução para identificar problemas de hardware e software.

Observe que as verificações Acessibilidade do sistema e Acessibilidade de instâncias foram aprovadas.

 

Selecione a guia Monitoramento.

Essa guia exibe as métricas do Amazon CloudWatch para sua instância. Atualmente, não há muitas métricas para exibir porque a instância foi executada recentemente.

Você pode clicar no ícone de três pontos em qualquer grafo e selecionar Ampliar para exibir uma visão ampliada da métrica escolhida.

 O Amazon EC2 envia as métricas das instâncias do EC2 ao Amazon CloudWatch. Por padrão, o monitoramento básico (cinco minutos) está ativado. Você também pode ativar o monitoramento detalhado (um minuto).

 

No menu Ações  no topo do console, selecione Monitor and troubleshoot (Monitorar e solucionar problemas)  Obter log do sistema.

O log do sistema exibe a saída do console da instância, que é uma ferramenta essencial para o diagnóstico de problemas. É especialmente útil para resolver problemas de kernel e problemas de configuração de serviço que possam fazer com que uma instância seja encerrada ou torne-se inalcançável antes de seu daemon SSH ser iniciado. Se você não vir um log do sistema, aguarde alguns minutos e, em seguida, tente novamente.

 

Role até a saída e observe que o pacote HTTP foi instalado com base nos dados do usuário que você adicionou quando criou a instância.

Saída do console

Selecione Cancelar.

 

Certifique-se de que Web Server ainda esteja selecionado. Depois, no menu Ações , selecione Monitor and troubleshoot (Monitorar e solucionar problemas)  Obter captura de tela da instância.

Abaixo você verá como seria seu console da instância do Amazon EC2 se uma tela estivesse anexada a ele.

Captura de tela

 

 Se você não conseguir acessar a instância via SSH ou RDP, poderá fazer uma captura de tela e visualizá-la como imagem. Isso fornece visibilidade do status da instância e permite uma solução de problemas mais rápida.

 

Selecione Cancelar.

 Parabéns! Você explorou várias maneiras de monitorar sua instância.

 

Tarefa 3: Atualizar o grupo de segurança e acessar o servidor web
Ao iniciar a instância EC2, você forneceu um script que instalou um servidor web e criou uma página da web simples. Nesta tarefa, você acessará o conteúdo do servidor web.

 

Certifique-se de que Web Server ainda esteja selecionado.  Selecione a guia Detalhes.

 

Copie o endereço IPv4 público da instância para a área de transferência.

 

Abra uma nova guia no navegador da web, cole o endereço IP que você acabou de copiar e pressione Enter.

Pergunta: você consegue acessar seu servidor web? Por que não?

No momento, você não consegue acessar o servidor web porque o grupo de segurança não permite o tráfego de entrada na porta 80, usada para solicitações HTTP da web. Esta é uma demonstração do uso de um grupo de segurança como firewall para restringir o tráfego de rede permitido para dentro e para fora de uma instância.

Para corrigir isso, atualize o grupo de segurança para permitir o tráfego na web na porta 80.

 

Mantenha a guia do navegador aberta, mas volte para a guia EC2 Console (Console do EC2).

 

No painel de navegação à esquerda, escolha Grupos de segurança.

 

Selecione  Web Server security group (Grupo de segurança do servidor Web).

 

Selecione a guia Regras de entrada.

No momento, o grupo de segurança não tem regras de entrada.

 

Selecione Editar regras de entrada, selecione Adicionar regra e, depois, configure:

Tipo: HTTP

Origem: Anywhere-IPv4

Selecione Salvar regras.

 

Volte para a guia do servidor web aberto anteriormente e atualize  a página.

Você deve ver a mensagem Hello From Your Web Server! (Olá do seu servidor web!).

 

 Parabéns! Você modificou com êxito o grupo de segurança para permitir tráfego HTTP na instância do Amazon EC2.

 

Tarefa 4: Redimensionar a instância: tipo de instância e volume do EBS
Conforme suas necessidades mudam, você pode observar que sua instância está superutilizada (muito pequena) ou subutilizada (muito grande). Se isso acontecer, você poderá alterar o tipo de instância. Por exemplo, se uma instância t2.micro for muito pequena para sua carga de trabalho, você poderá alterá-la para uma instância m5.medium. Da mesma forma, você também poderá alterar o tamanho de um disco.

 

Interromper a instância
Antes de redimensionar uma instância, você deve interrompê-la.

 Quando você interrompe uma instância, ela é desligada. Não há cobrança de runtime para uma instância do EC2 interrompida, mas a cobrança de armazenamento para volumes do Amazon EBS anexados é mantida.

No Console de gerenciamento do EC2, no painel de navegação à esquerda, selecione Instâncias e escolha a instância  Web Server.

 

No menu Estado da instância , selecione Interromper instância.

 

Escolha Interromper.

A instância fará um desligamento normal e, depois, interromperá a execução.

 

Aguarde até que o campo Estado da instância exiba:  Interrompida.

 

Altere o tipo de instância e ative a proteção contra interrupção
Selecione a instância Web Server e, no menu Ações , escolha Configurações da instância  Alterar tipo de instância e configure:

Tipo de instância: t2.small

Selecione Aplicar.

Quando a instância for iniciada novamente, ela será executada como uma t2.small, que tem duas vezes mais memória que uma instância t2.micro. OBSERVAÇÃO: talvez você não possa usar outros tipos de instância neste laboratório.

 

Selecione a instância Web Server e, no menu Ações , escolha Configurações de instância  Alterar proteção contra interrupção. Selecione Ativar e Salvar para fazer a alteração.

 Ao interromper uma instância, ela é desligada. Quando você iniciar a instância posteriormente, normalmente ela será migrada para um novo computador host subjacente e receberá um novo endereço IPv4 público. Uma instância retém seu endereço IPv4 privado. Quando você interrompe uma instância, ela não é excluída. Os volumes do EBS e os dados nesses volumes são retidos. 

 

Redimensionar o volume do EBS
Com a instância Web Server ainda selecionada, selecione a guia Armazenamento, selecione o nome do ID do volume e marque a caixa de seleção ao lado do volume exibido.

 

No menu Ações , selecione Modificar volume.

Atualmente, o volume do disco é de 8 GiB. Você aumentará o tamanho desse disco.

 

Altere o tamanho para: 10 OBSERVAÇÃO: a criação de volumes do Amazon EBS maiores que 10 GB pode estar restrita neste laboratório.

 

Selecione Modificar.

 

Selecione Modificar novamente para confirmar e aumentar o tamanho do volume.

 

Iniciar a instância redimensionada
Neste momento, você iniciará a instância novamente, agora com mais memória e mais espaço em disco.

No painel de navegação à esquerda, selecione Instâncias.

 

Selecione a instância Web Server.

 

No menu Estado da instância , selecione Iniciar instância.

 Parabéns! Você redimensionou com êxito sua instância do Amazon EC2. Nessa tarefa, você alterou o tipo de instância de t2.micro para t2.small. Você também modificou o volume do disco-raiz de 8 GiB para 10 GiB.

 

Tarefa 5: Explorar os limites do EC2
O Amazon EC2 oferece recursos diferentes que você pode usar. Esses recursos incluem imagens, instâncias, volumes e snapshots. Ao criar uma conta AWS, existem limites padrão quanto a esses recursos, de acordo com a região.

 

No Console de Gerenciamento da AWS, na caixa de pesquisa ao lado de  Serviços, pesquise e selecione Service Quotas.

 

Selecione Serviços da AWS no menu de navegação e, na barra de pesquisa Localizar serviços dos serviços da AWS, procure por ec2 e selecione Amazon Elastic Compute Cloud (Amazon EC2).

 

Na barra de pesquisa Encontrar cotas, procure por running on-demand, mas não selecione. Em vez disso, observe a lista filtrada de cotas de serviço que correspondem aos critérios.

Há limites na quantidade e nos tipos de instâncias que podem ser executadas em uma região. Por exemplo, há um limite para o número de instâncias Running On-Demand Standard... (Execução do padrão sob demanda) que você pode executar nesta região. Ao executar uma instância, a solicitação não deve fazer com que seu uso exceda os limites de instâncias definidos atualmente nessa região.

Se você é o proprietário da conta da AWS, poderá solicitar um aumento para muitos desses limites.

 

Tarefa 6: Testar a proteção contra interrupção
É possível interromper a instância quando não precisar de acesso, mas você ainda precisará retê-la. Nesta tarefa, você aprenderá a usar a proteção contra interrupção.

 

No Console de Gerenciamento da AWS, na caixa de pesquisa ao lado de  Serviços, pesquise e selecione EC2 para retornar ao console do EC2.

 

No painel de navegação à esquerda, selecione Instâncias.

 

Selecione a instância Web Server e, no menu Estado da instância , selecione Interromper instância.

 

Depois, selecione Interromper.

Observe que há uma mensagem informando: Failed to stop the instance i-1234567xxx. The instance 'i-1234567xxx' may not be stopped. Modify its 'disableApiTermination' instance attribute and try again (Falha ao interromper a instância i-1234567xxx. Não é possível interromper a instância “i-1234567xxx”. Modifique o atributo “disableApiTermination” da instância e tente novamente).

Isso mostra que a proteção contra interrupção que você ativou anteriormente neste laboratório agora está fornecendo uma proteção para evitar a interrupção acidental de uma instância. Se você realmente deseja interromper a instância, precisa desativar a proteção contra interrupção.

 

No menu Ações , selecione Configurações de instância  Alterar proteção contra interrupção.

 

Remova a seleção ao lado de  Ativar.

 

Selecione Salvar.

Agora é possível interromper a instância.

 

Selecione a instância Web Server novamente e, no menu Estado da instância , escolha Interromper instância.

 

Escolha Interromper.

 Parabéns! Você testou com êxito a proteção contra interrupção e interrompeu a instância.

 

Envio do trabalho
Para registrar seu progresso, selecione Enviar no topo destas instruções.

 

Quando solicitado, selecione Sim.

Depois de alguns minutos, o painel de notas é exibido e mostra quantos pontos você obteve em cada tarefa. Se os resultados não forem exibidos após alguns minutos, selecione Notas no topo destas instruções.

  Importante:  algumas das verificações feitas no processo de envio deste laboratório só fornecerão crédito a você pelo menos cinco minutos após a conclusão da ação. Se você não receber crédito no primeiro envio, aguarde alguns minutos e envie novamente para receber crédito por esses itens.

 Dica: você pode enviar seu trabalho várias vezes. Depois de fazer as alterações, selecione Enviar novamente. Seu último envio é registrado para o laboratório.

 

Para ver o feedback detalhado sobre seu trabalho, selecione Relatório de envio.

 Dica: se você não tiver recebido a pontuação total em alguma verificação, poderá haver detalhes úteis no relatório de envio.

 

Laboratório concluído
Parabéns! Você concluiu o laboratório.

Selecione Encerrar laboratório no topo da página e Sim para confirmar que você deseja encerrar o laboratório.  

Um painel “End Lab” (Encerrar laboratório) aparecerá indicando “You may close this message box now.” (Você pode fechar esta caixa de mensagem agora).

 

Selecione o X no canto superior direito para fechar o painel.
