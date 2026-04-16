Laboratório 1: Introdução ao AWS IAM
O AWS Identity and Access Management (AWS IAM) é um serviço da web que possibilita a clientes da Amazon Web Services (AWS) gerenciar usuários e permissões de usuário na AWS. Com o IAM, você pode gerenciar de forma centralizada os usuários, as credenciais de segurança (como as chaves de acesso) e as permissões que controlam quais recursos da AWS os usuários podem acessar.

 

Visão geral e objetivos do laboratório
Este laboratório demonstrará como:

Visão geral do laboratório

Como explorar usuários e grupos do IAM pré-criados.
Como inspecionar políticas do IAM, conforme aplicadas aos grupos pré-criados.
Como seguir um cenário real adicionando usuários a grupos com recursos específicos ativados.
Como localizar e usar a URL de login do IAM.
Como testar os efeitos das políticas no acesso ao serviço.
 

Restrições de serviço da AWS
Neste ambiente de laboratório, o acesso aos serviços e às ações de serviços da AWS pode ser restrito aos necessários para concluir as instruções do laboratório. Você poderá encontrar erros se tentar acessar outros serviços ou executar ações além das descritas neste laboratório.

 

AWS Identity and Access Management
O AWS Identity and Access Management (IAM) pode ser usado para:

Gerenciar usuários do IAM e o acesso: você pode criar usuários e atribuir a eles credenciais de segurança individuais (chaves de acesso, senhas e dispositivos de autenticação multifator). É possível gerenciar as permissões para controlar quais operações um usuário pode executar.

Gerenciar perfis do IAM e as permissões: um perfil do IAM é semelhante a um usuário, já que é uma identidade da AWS com políticas de permissão que definem o que a identidade pode e não pode fazer na AWS. Porém, a finalidade de uma função é poder ser assumida por qualquer pessoa que necessite dela e não associada exclusivamente a um único indivíduo.

Gerenciar usuários federados e as permissões: você pode ativar a federação de identidades para permitir que os usuários existentes na sua empresa acessem o Console de Gerenciamento da AWS, chamem as APIs da AWS e acessem recursos, sem precisar criar um usuário do IAM para cada identidade.

 

Duração
O laboratório levará aproximadamente 40 minutos para ser concluído.

 

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

 

Tarefa 1: Explorar usuários e grupos
Nesta tarefa, você explorará os usuários e grupos que foram criados para você no IAM.

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione IAM para abrir o console do IAM.

    

No painel de navegação à esquerda, selecione Usuários.

Os seguintes usuários do IAM foram criados para você:

user-1

user-2

user-3

 

Escolha o link user-1.

Isso exibe a página de resumo do user-1. A guia Permissões será exibida.

 

Observe que user-1 não tem permissões.

 

Escolha a guia Grupos.

O user-1 também não faz parte de nenhum grupo.

 

Selecione a guia Credenciais de segurança.

O user-1 recebe uma Senha do console.

 

No painel de navegação à esquerda, selecione Grupos de usuários.

   Os seguintes grupos já foram criados para você:

EC2-Admin

EC2-Support

S3-Support

  

Escolha o link do grupo EC2-Support.

 A página de resumo do grupo EC2-Support será exibida.

   

Selecione a guia Permissões.

 Esse grupo tem uma política gerenciada associada a ele, chamada AmazonEC2ReadOnlyAccess. As políticas gerenciadas são políticas predefinidas (criadas pela AWS ou pelos administradores) que podem ser associadas a usuários e grupos do IAM. Quando a política é atualizada, as alterações são imediatamente aplicadas a todos os usuários e grupos vinculados a ela.

 

Ao lado da política AmazonEC2ReadOnlyAccess, selecione o ícone de mais (+) para exibir os detalhes da política.

Observação: uma política define quais ações são permitidas ou negadas para recursos específicos da AWS. 

Essa política concede permissão para as ações List (Listar) e Describe (Descrever) informações sobre o EC2, Elastic Load Balancing, CloudWatch e Auto Scaling. Essa capacidade de visualizar recursos, mas não os modificar, é ideal para ser atribuída à uma Função de suporte.

A estrutura básica das declarações de uma política do IAM é:

Efeito indica se deseja permitir ou negar as permissões.

Ação especifica as chamadas de API que podem ser feitas em um serviço da AWS (por exemplo, cloudwatch:ListMetrics).

Recursos define o escopo das entidades cobertas pela regra de política (por exemplo, um bucket específico do Amazon S3 ou uma instância do Amazon EC2; ou *, que indica qualquer recurso).

 

Selecione o ícone de menos (-) para ocultar os detalhes da política.

 

No painel de navegação à esquerda, selecione Grupos de usuários.

 

Selecione o grupo S3-Support e selecione a guia Permissões.

 O grupo S3-Support tem a política AmazonS3ReadOnlyAccess anexada.

 

Selecione o ícone de mais (+) para exibir os detalhes da política.

 Essa política concede permissões para as ações [Obter] e [Listar] recursos no Amazon S3.

 

Selecione o ícone de menos (-) para ocultar os detalhes da política.

 

No painel de navegação à esquerda, selecione Grupos de usuários.

 

Selecione o link do grupo EC2-Admin e escolha a guia Permissões. 

 Esse grupo é um pouco diferente dos outros dois. Em vez de uma política gerenciada, ele tem uma política em linha, que é uma política atribuída a apenas um usuário ou grupo. As políticas em linha são normalmente usadas para aplicar permissões para situações pontuais.

 

Selecione o ícone de mais (+) para exibir os detalhes da política.

Essa política concede permissão para ação Describe (Descrever) para visualizar informações sobre o Amazon EC2 e para as ações Start (Iniciar) e Stop (Interromper) instâncias.

 

Selecione o ícone de menos (-) para ocultar os detalhes da política.
 

Cenário de negócios
Para o restante deste laboratório, você trabalhará com esses Usuários e Grupos para ativar permissões que oferecem suporte ao seguinte cenário de negócios:

Sua empresa está aumentando o uso da Amazon Web Services e está usando muitas instâncias do Amazon EC2 e uma grande quantidade de armazenamento do Amazon S3. Você deseja conceder acesso a novos membros da equipe de acordo com suas funções de trabalho:

Usuário	No grupo	Permissões
user-1	S3-Support	Acesso de somente leitura ao Amazon S3
user-2	EC2-Support	Acesso de somente leitura ao Amazon EC2
user-3	EC2-Admin	Visualizar, iniciar e interromper instâncias do Amazon EC2
|

Tarefa 2: Adicionar usuários a grupos
Recentemente, você contratou o user-1 para uma função de suporte ao Amazon S3. Você o adicionará ao grupo S3-Support para que ele herde as permissões necessárias por meio da política AmazonS3ReadOnlyAccess associada.

 Você pode ignorar todos os erros indicando “não autorizado” que aparecem durante essa tarefa. Eles são causados porque sua conta de laboratório tem permissões limitadas, mas isso não impede que você finalize o laboratório.

 

Adicionar user-1 ao grupo S3-Support
No painel de navegação à esquerda, selecione Grupos de usuários.

 

Escolha o link do grupo S3-Support.

 

Escolha a guia Usuários.

 

Na guia Usuários, selecione Adicionar usuários.

 

Na janela Adicionar usuários ao S3-Support, configure o seguinte:

Selecione  user-1.

Na parte inferior da tela, escolha Adicionar usuários.

Na guia Usuários, você verá que user-1 foi adicionado ao grupo.

 

Adicionar user-2 ao grupo EC2-Support
Você contratou o user-2 para uma função de suporte ao Amazon EC2.

 

Seguindo etapas semelhantes às anteriores, adicione user-2 ao grupo EC2-Support.

O user-2 agora fará parte do grupo EC2-Support.

 

Adicionar o user-3 ao grupo EC2-Admin
Você contratou o user-3 como administrador do Amazon EC2 para gerenciar suas instâncias do EC2.

 

Seguindo etapas semelhantes às anteriores, adicione user-3 ao grupo EC2-Admin.

O user-3 agora fará parte do grupo EC2-Admin.

 

No painel de navegação à esquerda, selecione Grupos de usuários.

Cada grupo deve ter um 1 na coluna Usuários, indicando o número de usuários de cada grupo.

Se o número 1 não aparecer ao lado de cada grupo, releia as instruções acima e verifique se cada usuário está atribuído a um grupo de usuários, conforme mostrado na tabela na seção Cenário de negócios.

 

Tarefa 3: Fazer login e testar usuários
Nesta tarefa, você testará as permissões de cada usuário do IAM.

 

No painel de navegação à esquerda, escolha Painel.

Um link de URL de login para usuários do IAM nesta conta é exibido à direita. Ele será semelhante a: https://123456789012.signin.aws.amazon.com/console

Esse link pode ser usado para entrar na conta da AWS que você está usando no momento.

 

Copie o URL de login para usuários do IAM nesta conta em um editor de texto.

 

Abra uma janela privada (anônima).

Mozilla Firefox

Selecione as barras de menu  no canto superior direito da tela
Selecione Nova janela privada
Google Chrome

Selecione as reticências  no canto superior direito da tela
Selecione Nova janela anônima
Microsoft Edge

Selecione as reticências  no canto superior direito da tela
Selecione Nova janela InPrivate
Microsoft Internet Explorer

Selecione a opção de menu Ferramentas

Selecione Navegação InPrivate

 

Cole o link de login para usuários do IAM na barra de endereço da sessão privada do navegador e pressione Enter.

Agora, faça login como user-1, que foi contratado como parte da equipe de suporte de armazenamento do Amazon S3.

 

Faça login com as credenciais:

Nome do usuário do IAM: user-1

Senha: Lab-Password1

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione S3 para abrir o console do S3.

 

Escolha o nome do bucket existente na conta e navegue pelo conteúdo.

Como faz parte do grupo S3-Support no IAM, o usuário tem permissão para visualizar uma lista de buckets do Amazon S3 e o conteúdo.

Observação: o bucket não contém nenhum objeto.

Agora, teste se o usuário consegue acessar o Amazon EC2.

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione EC2 para abrir o console do EC2.

 

No painel de navegação à esquerda, selecione Instâncias.

Não há nenhuma instância listada. Em vez disso, aparece a seguinte mensagem: You are not authorized to perform this operation (Você não tem autorização para realizar esta operação). Isso ocorre porque o usuário não recebeu permissões para acessar o Amazon EC2.

Agora, faça login como user-2, que foi contratado como responsável pelo suporte ao Amazon EC2.

 

Conclua as ações a seguir para desconectar o user-1 do Console de Gerenciamento da AWS:

No topo da tela, selecione user-1.
Escolha Sair.
captura de tela

 

Cole o link de login para usuários do IAM na barra de endereço da guia privada do navegador e pressione Enter.

Observação: esse link deve estar no seu editor de texto.

 

Faça login com as credenciais:

Nome do usuário do IAM: user-2

Senha: Lab-Password2

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione EC2 para abrir o console do EC2.

 

No painel de navegação à esquerda, selecione Instâncias.

Agora, você consegue ver uma instância do Amazon EC2 porque tem permissões de somente leitura. No entanto, você não pode fazer nenhuma alteração nos recursos do Amazon EC2.

 Se não for possível ver uma instância do Amazon EC2, sua Região poderá estar incorreta. No canto superior direito da tela, expanda o menu Região e selecione a Região que você anotou no início do laboratório (por exemplo, Norte da Virgínia).

 

Selecione a instância chamada  LabHost.
 

No menu Estado da instância, selecione Interromper instância.

 

Na janela Interromper instância, selecione Interromper.

Você receberá a seguinte mensagem de erro: You are not authorized to perform this operation (Você não tem autorização para realizar esta operação). Isso demonstra que a política permite apenas que você visualize as informações, sem fazer alterações.

 

Selecione o X para fechar a mensagem Failed to stop the instance (Falha ao interromper a instância).

Depois, verifique se o user-2 pode acessar o Amazon S3.

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione S3 para abrir o console do S3.

Você receberá a mensagem Você não tem permissões para listar buckets porque o user-2 não tem permissões para acessar o Amazon S3.

Agora, faça login como user-3, que foi contratado como administrador do Amazon EC2.

 

Conclua as ações a seguir para desconectar o user-2 do Console de Gerenciamento da AWS:

No topo da tela, selecione user-2
Escolha Sair.
captura de tela

 

Cole o link de login de usuários do IAM na janela privada e pressione Enter.

 

Cole o link de login na barra de endereço da guia privada do navegador da web novamente. Se ele não estiver na área de transferência, copie-o do editor de texto no qual você o armazenou anteriormente.

 

Faça login com as credenciais:

Nome do usuário do IAM: user-3

Senha: Lab-Password3

 

Na caixa de pesquisa à direita de  Serviços, procure e selecione EC2 para abrir o console do EC2.

 

No painel de navegação à esquerda, selecione Instâncias.

Como administrador do EC2, agora você deve ter permissões para interromper a instância do Amazon EC2.

Selecione a instância chamada  LabHost.

 Se não for possível ver uma instância do Amazon EC2, sua Região poderá estar incorreta. No canto superior direito da tela, expanda o menu Região e selecione a Região que você anotou no início do laboratório (por exemplo, Norte da Virgínia).

 

No menu Estado da instância, selecione Interromper instância.

 

Na janela Interromper instância, escolha Interromper.

A instância entrará no estado interrompendo e será desligada.

 

Feche a janela privada do navegador.

 

Envio do trabalho
Para registrar seu progresso, selecione Enviar no topo destas instruções.

  Importante:  algumas das verificações feitas no processo de envio deste laboratório só fornecerão crédito a você pelo menos cinco minutos após a conclusão da ação. Se você não receber crédito no primeiro envio, aguarde alguns minutos e envie novamente para receber crédito por esses itens. 

 

Quando solicitado, selecione Sim.

Depois de alguns minutos, o painel de notas é exibido e mostra quantos pontos você obteve em cada tarefa. Se os resultados não forem exibidos após alguns minutos, selecione Notas no topo destas instruções.

 Dica: você pode enviar seu trabalho várias vezes. Depois de fazer as alterações, selecione Enviar novamente. Seu último envio é registrado para o laboratório.

 

Para ver o feedback detalhado sobre seu trabalho, selecione Relatório de envio.

 Dica: se você não tiver recebido a pontuação total em alguma verificação, poderá haver detalhes úteis no relatório de envio.

 

Laboratório concluído 
Parabéns! Você concluiu o laboratório.

 

Selecione  Encerrar laboratório no topo da página e Sim para confirmar que você deseja encerrar o laboratório.

Um painel exibe a mensagem: You may close this message box now... (Você pode fechar esta caixa de mensagem agora)

 

Selecione o X no canto superior direito para fechar o painel.
 

Conclusão
 Parabéns! Você concluiu com sucesso as tarefas:

Explorou os usuários e grupos do IAM pré-criados.
Inspecionou as políticas do IAM conforme aplicadas aos grupos pré-criados.
Seguiu um cenário real para adicionar usuários a grupos com recursos específicos habilitados.
Localizou e usou a URL de login do IAM
Testou os efeitos das políticas no acesso ao serviço
 

© 2023, Amazon Web Services, Inc. e suas afiliadas. Todos os direitos reservados. Este trabalho não pode ser reproduzido nem redistribuído, parcial ou integralmente, sem a permissão prévia por escrito da Amazon Web Services, Inc. A cópia, empréstimo ou venda para fins comerciais é proibida.