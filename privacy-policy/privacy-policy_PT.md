# Política de Privacidade do Popt

*Este documento é uma tradução da versão em inglês. Somente a versão em inglês, [privacy-policy_EN.md](privacy-policy_EN.md), é juridicamente vinculativa.*

Última atualização: 2 de novembro de 2026

## Resumo

O Popt é um app que coloca a privacidade em primeiro lugar. O conteúdo que você coloca no Popt é criptografado no seu dispositivo antes de ser enviado a qualquer lugar, com chaves que não temos (criptografia de ponta a ponta de verdade). Não conseguimos ler suas tarefas, notas, diário, fotos, biblioteca, publicações ou mensagens, e ninguém que invada nossos servidores consegue. O que nossos servidores veem é a parte estrutural: quais contas compartilharam conteúdo, as datas de criação e modificação do conteúdo, e seu nome de exibição e avatar no Popt, para que você possa ver quem está em um grupo com você mesmo sem ser amigo dessa pessoa.

Não usamos seus dados para treinar IA. Não os vendemos a terceiros. Não traçamos seu perfil nem exibimos anúncios de nenhum tipo. O app se conecta aos nossos próprios servidores para sincronizar e fazer backup do seu conteúdo em todos os seus dispositivos, e para viabilizar o compartilhamento, as mensagens e nosso serviço de busca de mídia para adicionar itens à sua biblioteca do Popt. O app também se comunica com serviços de terceiros que prestam serviços essenciais para nós:

* **Apple:** busca de mapas, lugares e música, tudo coberto pelas rigorosas políticas de privacidade da Apple.
* **Google:** gerenciamento de contas e autenticação com o Firebase. Hospedagem de servidores e banco de dados no Google Cloud.
* **PowerSync:** seus dados passam pelos servidores do PowerSync para chegar aos seus dispositivos.
* **Cloudflare:** suas fotos e arquivos criptografados são armazenados no Cloudflare R2. O app envia e baixa diretamente do R2.

Esses terceiros não têm acesso ao seu conteúdo, que de qualquer forma está totalmente criptografado.

Você pode exportar tudo, apagar tudo e verificar nossas afirmações com as ferramentas abertas que publicamos.

## Quem somos

O Popt é feito pela Skile SA, uma empresa com sede na Suíça. A Skile SA é a controladora dos dados do Popt: decidimos o que o app coleta e por quê, e respondemos por isso. Nossa jurisdição é a Suíça. O Popt é usado na Europa, nos Estados Unidos e em outros lugares, e nos esforçamos para cumprir as leis de proteção de dados mais restritivas. Hoje, essa lei é o Regulamento Geral de Proteção de Dados da UE, o RGPD (GDPR); por isso, em qualquer país em que você esteja, você tem as proteções do RGPD.

Você pode falar conosco sobre qualquer ponto desta política pelo e-mail support@popt.com. Nosso endereço é Skile SA, Rue de Riant-Coteau 7, 1196 Gland, Suíça.

Não temos parceiros de publicidade, corretores de dados nem empresa de análise de uso por trás do app. As únicas outras partes envolvidas são os provedores de serviços listados em [Serviços aos quais o app se conecta](#serviços-aos-quais-o-app-se-conecta), e nomeamos cada um deles.

## Como o seu conteúdo é protegido

Tudo o que você escreve, fotografa ou salva no Popt é criptografado no seu dispositivo antes de sair dele, com chaves que só você e as pessoas com quem você compartilha possuem. Nossos servidores armazenam e retransmitem esse conteúdo criptografado. Usamos criptografia padrão do setor, nada de invenção própria: AES-256 para seu conteúdo e arquivos, e chaves de curva elíptica para compartilhá-los. O projeto completo é público e pode ser verificado de forma independente (veja [Verifique por conta própria](#verifique-por-conta-própria)).

**Suas chaves nunca saem do seu dispositivo em forma legível.** Uma cópia bloqueada fica nos nossos servidores para que um novo dispositivo possa ser configurado, e a única coisa capaz de desbloqueá-la é o seu **código de recuperação**, gerado no seu dispositivo e nunca visto por nós. O código de recuperação é o único segredo que você precisa guardar. Se você perdê-lo e perder todos os dispositivos com sessão iniciada, não conseguimos recuperar seu conteúdo para você.

**O conteúdo compartilhado** é criptografado exatamente para as pessoas do compartilhamento, e cada uma delas tem a própria chave de acesso a ele. Quando alguém é removido, o que é compartilhado dali em diante é criptografado com uma nova chave que essa pessoa não tem.

**Fotos e arquivos** são criptografados no seu dispositivo antes do envio, assim como seus nomes, tipos e dimensões. Cada arquivo tem a própria chave, que viaja dentro do item criptografado ao qual pertence; assim, uma foto só pode ser lida por quem pode ler a nota, a lista ou a publicação em que ela está. No armazenamento, um arquivo é só um nome aleatório e um bloco de dados criptografado.

**As notificações push** também são criptografadas. A prévia em uma notificação (o nome de um item, as primeiras palavras de um comentário) é selada para que só os dispositivos de destino possam abri-la. As notificações passam pelo Firebase Cloud Messaging, do Google, e depois pelo serviço push da Apple; os dois, como o nosso próprio servidor de notificações, veem os identificadores das contas de origem e de destino e o tipo de evento (mensagem, publicação, novo compartilhamento...), nunca o que ela diz.

### O que não é criptografado

Um servidor que armazena e entrega conteúdo criptografado ainda precisa saber a qual conta ele pertence, com quais contas ele é compartilhado, qual dispositivo o atualizou por último e quando ele foi criado ou atualizado. Estas são as informações que nossos servidores conseguem ler, e o motivo de cada uma existir:

- **Identificadores de conta.** Para que o servidor entregue cada item aos dispositivos certos e a mais ninguém.
- **Quando cada item foi criado, alterado ou apagado, e quais dispositivos o atualizaram por último.** É assim que dois dispositivos que editaram a mesma coisa offline são conciliados: sem isso, o servidor não saberia qual alteração é a mais recente, e edições seriam perdidas. O identificador do dispositivo é o identificador por fornecedor (IDFV) da Apple: ele é específico do Popt naquele dispositivo, não é o identificador de publicidade e não pode ser usado para reconhecer você em outros apps. Ele é redefinido quando o Popt é removido do dispositivo.
- **Como o conteúdo é agrupado.** A qual item de nível superior (uma lista, uma nota, uma publicação, um projeto) cada parte pertence. O servidor armazena, entrega e protege o conteúdo como itens inteiros, então precisa saber onde um termina e o próximo começa. A estrutura dentro de um item, qual linha fica sob qual, é criptografada.
- **Seu nome, seu status e seu avatar no Popt.** Eles ficam legíveis para que todos em uma publicação ou lista compartilhada possam ver quem mais está ali, incluindo pessoas que não são suas amigas, e para que alguém que você convida possa ver quem está convidando. O app avisa isso onde você edita seu perfil.
- **Quais conversas você silenciou, e a data em que abriu cada uma pela última vez.** Nosso servidor de notificações lê essas informações para parar de notificar você sobre uma conversa que você silenciou, e para não alertar sobre algo que você já viu. Ele registra identificadores de conversas, não conteúdos.
- **Quanto armazenamento você usa.** A Cloudflare, onde os arquivos criptografados ficam armazenados, vê o tamanho de cada um, como qualquer serviço de armazenamento de arquivos. Somamos esse total por conta para aplicar o limite de armazenamento do seu plano, e liberamos um arquivo assim que nada mais aponta para ele.

## Os dados que coletamos e por quê

Coletamos o mínimo de que o app precisa para funcionar, e nada para saber mais sobre você.

- **Seu endereço de e-mail.** Para iniciar sua sessão e reconhecer você quando nos escreve. Ele vem de você ao iniciar a sessão, ou da Apple ou do Google quando você inicia a sessão com eles (Iniciar sessão com a Apple pode escondê-lo atrás do relay da Apple). Ele fica no Firebase Authentication; nosso próprio banco de dados guarda apenas um hash dele.
- **Seu nome, seu status e seu avatar no Popt.** Para que seus amigos reconheçam você. Só o nome é obrigatório. Armazenados em texto legível, como explicado acima.
- **Seu conteúdo criptografado e seus metadados.** Para sincronizar entre seus dispositivos e com as pessoas com quem você compartilha.
- **Identificadores anônimos de dispositivo.** Para notificar seus dispositivos e distingui-los. Usa o `identifierForVendor` da Apple, que preserva a privacidade.
- **Seus recibos de assinatura.** Para desbloquear o Popt Pro em todos os seus dispositivos. Eles vêm da Apple quando você assina; nunca vemos os dados de pagamento.
- **Registros de requisições** (endereço IP, horário, caminho). Para manter o serviço funcionando e investigar abusos, como qualquer servidor web.
- **Denúncias de abuso.** Para agir contra comportamentos nocivos. Elas vêm das pessoas que as enviam.

**O que não coletamos:** sua data de nascimento, seus contatos, sua biblioteca de fotos, sua localização, análises de como você usa o app ou um identificador de publicidade.

**Bases legais.** Processamos seus dados para prestar o serviço que você pediu (o contrato com você), porque você escolheu compartilhar algo ou conceder uma permissão (consentimento, que você pode retirar), para manter o serviço seguro e responder a denúncias de abuso (nosso interesse legítimo, e em parte uma obrigação legal), e para cumprir obrigações contábeis e fiscais (obrigação legal).

**Nunca vendemos dados, nunca os compartilhamos para publicidade e nunca usamos seu conteúdo para treinar nada.**

## Serviços aos quais o app se conecta

Esta é a lista completa. Se o app se comunica com algo, está aqui.

### Servidores do Popt

Eles rodam no Google Cloud, nos Estados Unidos, e as fotos e arquivos criptografados ficam armazenados na Cloudflare, também nos Estados Unidos. Dizemos isso com clareza porque a localização importa, e porque aqui ela importa muito pouco: o que fica nesses servidores é conteúdo que não conseguimos ler, mais os metadados listados acima. Seu conteúdo é tão ilegível em um data center nos EUA quanto seria em um na Suíça, e os metadados são protegidos pelas mesmas regras onde quer que estejam.

Todos ficam sob `*.popt.com`. Veja o que cada recurso do app envia:

- **Sincronização entre seus dispositivos.** Seu conteúdo criptografado, os metadados listados acima e a prova de que sua sessão está iniciada.
- **Amigos e compartilhamento.** Os identificadores das contas conectadas como amigas, os identificadores das contas que fazem parte de cada lista, projeto ou publicação compartilhada, e cópias bloqueadas das chaves compartilhadas.
- **Mensagens.** Suas mensagens criptografadas e os identificadores das contas dos dois lados de uma conversa.
- **Notificações.** O endereço que a Apple nos dá para alcançar seu dispositivo, os identificadores das contas de remetente e destinatários, e a prévia criptografada.
- **Popt Pro.** O recibo da Apple da sua assinatura, para que o Pro possa ser desbloqueado em todos os seus dispositivos.
- **Início de sessão por e-mail.** Seu endereço de e-mail, para que possamos enviar o código de uso único.
- **Adicionar à biblioteca.** Sua busca por um livro, filme, série, jogo ou podcast, com seu idioma e sua faixa etária. As buscas não são registradas.
- **Publicar um item da biblioteca como link.** O item que você escolheu publicar. O item publicado em si não é vinculado à sua conta.
- **Denunciar abusos.** Sua denúncia, criptografada e legível só pela nossa equipe de análise.
- **Avatares.** O estilo que você escolheu e um número aleatório a partir do qual o avatar é desenhado. Nada sobre você.

Nossos servidores guardam registros de requisições padrão por 30 dias: qual endereço chamou qual recurso, e quando.

### Serviços do Google

A [política de privacidade do Google](https://policies.google.com/privacy) se aplica a todos eles. O Firebase e o Google Cloud publicam cada um a própria página, com links abaixo.

- **Início de sessão ([Firebase Authentication](https://firebase.google.com/support/privacy)).** Guarda seu endereço de e-mail e como você inicia a sessão. Com Fazer login com o Google, também o nome e a foto da sua conta do Google.
- **Prova de que o app é genuíno ([Firebase App Check](https://firebase.google.com/support/privacy)).** Antes de nossos servidores responderem, o app prova que é uma cópia real do Popt rodando em um dispositivo real. O Google vê essa prova, não para que serve a requisição.
- **Entrega de push ([Firebase Cloud Messaging](https://firebase.google.com/support/privacy)).** Retransmite nossas notificações ao serviço push da Apple. Guarda o endereço que a Apple nos dá para alcançar seu dispositivo. A notificação que ele retransmite é criptografada.
- **Hospedagem ([Google Cloud](https://cloud.google.com/terms/cloud-privacy-notice)).** Roda nossos servidores e nosso banco de dados nos Estados Unidos e, portanto, guarda tudo o que nossos servidores guardam.
- **YouTube.** Quando você salva um link do YouTube, seu dispositivo pede ao YouTube o título e a miniatura. Quando você reproduz um trailer dentro do app (a partir de 16 anos), o app carrega o player do YouTube, e o YouTube vê você como veria um visitante do seu site, cookies incluídos. O YouTube não tem política separada: a do Google o cobre.

### Serviços da Apple

A [política de privacidade da Apple](https://www.apple.com/legal/privacy/) se aplica a todos eles. Onde a Apple publica uma página para um serviço, o link está abaixo.

- **[Iniciar sessão com a Apple](https://www.apple.com/legal/privacy/data/en/sign-in-with-apple/).** A Apple nos informa seu endereço de e-mail, ou o endereço de relay privado que você escolheu para escondê-lo.
- **Notificações (o serviço Apple Push Notification).** Entrega nossas notificações ao seu dispositivo. A Apple transporta o envelope criptografado e não consegue lê-lo.
- **Popt Pro (a [App Store](https://www.apple.com/legal/privacy/data/en/app-store/)).** Sua assinatura é comprada da Apple e cobrada por ela. Uma compra é vinculada à sua conta do Popt por um token aleatório, e o recibo da Apple é o que nossos servidores verificam.
- **Lugares ([Apple Maps](https://www.apple.com/legal/privacy/data/en/apple-maps/)).** Buscar um lugar, mostrar o mapa e converter coordenadas em endereço, tudo isso vai do seu dispositivo para a Apple. As buscas são vinculadas a um identificador rotativo, não ao seu ID Apple nem à sua conta do Popt.
- **Música ([Apple Music](https://www.apple.com/legal/privacy/data/en/apple-music/) e [Shazam](https://www.apple.com/legal/privacy/data/en/music-recognition/)).** Buscar um álbum ou artista vai para o Apple Music. Reconhecer uma música envia uma breve impressão digital de áudio ao Shazam, não a gravação.
- **Faixa etária.** Pedida ao iOS no dispositivo, como descrito em [Crianças e idade](#crianças-e-idade). Ela vem da idade da sua [Conta Apple](https://www.apple.com/legal/privacy/data/en/apple-account/).


### PowerSync

A [política de privacidade do PowerSync](https://www.powersync.com/legal/privacy-policy) se aplica.

O PowerSync (JourneyApps) é o serviço que cuida da sincronização de descida do banco de dados do Popt para os seus dispositivos. Seus dispositivos se conectam a ele diretamente, com um token dos nossos servidores, nos Estados Unidos.

### Cloudflare R2

A [política de privacidade da Cloudflare](https://www.cloudflare.com/privacypolicy/) se aplica.

Suas fotos e arquivos criptografados ficam armazenados na Cloudflare, nos Estados Unidos. O app os envia e baixa diretamente, em um endereço de curta duração fornecido pelos nossos servidores; assim, a Cloudflare vê seu endereço IP, os bytes criptografados e seu tamanho, e uma chave de armazenamento que começa com o identificador da sua conta. Nunca um nome de arquivo, nunca o conteúdo.

### Wikipedia e Wikidata

A [política de privacidade da Wikimedia](https://foundation.wikimedia.org/wiki/Policy:Privacy_policy) se aplica.

Quando você adiciona um artista à sua biblioteca, seu dispositivo pergunta ao Wikidata qual artigo da Wikipedia pertence a esse artista e depois pede à Wikipedia o primeiro parágrafo. Eles veem seu endereço IP e o artista, nada sobre sua conta.

### Outros

Algumas requisições vão direto do seu dispositivo para o site ao qual um link aponta. Esse site vê seu endereço IP, como vê quando você o visita em qualquer navegador. Não conseguimos listar esses sites, porque eles dependem dos links que você salva.

- **Pré-visualizações de links.** Quando você salva ou cola um link, seu dispositivo busca aquela página para mostrar um título e uma imagem. Links do TikTok usam o endpoint de pré-visualização do TikTok. As imagens nos resultados de busca e nas pré-visualizações de links são carregadas dos seus hosts originais. Se você tiver uma sessão iniciada em um site no navegador do Popt, essas requisições de pré-visualização carregam os cookies daquele site.
- **Imagens de notificações.** Quando a publicação de um amigo inclui um link, seu dispositivo busca a imagem do link para mostrá-la na notificação.
- **O navegador do Popt** é um navegador web normal: os sites que você visita veem você como qualquer navegador mostraria. Seu histórico e seus cookies ficam no seu dispositivo, e um navegador aberto dentro de um cofre secreto não guarda nada.

## Serviços que usamos nos bastidores

Seu dispositivo nunca se conecta a estes. Nossos servidores sim, a partir do nosso endereço, e não repassam nenhuma identidade, conta ou endereço IP.

### Twilio SendGrid

A [política de privacidade da Twilio](https://www.twilio.com/en-us/legal/privacy) se aplica.

Envia o e-mail com o código de início de sessão e, portanto, recebe seu endereço de e-mail uma vez a cada início de sessão.

### TMDB

A [política de privacidade do TMDB](https://www.themoviedb.org/privacy-policy) se aplica.

Quando você busca um filme, uma série, um ator ou um diretor, nosso servidor encaminha as palavras que você digitou e seu idioma.

### Movie of the Night

A [política de privacidade do Movie of the Night](https://www.movieofthenight.com/privacy) se aplica.

Informa ao app onde um filme ou série pode ser assistido em streaming. Nosso servidor envia o número de catálogo do filme e seu país.

## Somente no seu dispositivo

Vários dos recursos mais inteligentes do Popt rodam inteiramente no seu telefone. Nada sobre eles é enviado para nós.

- **Classificar o que você digita.** Quando você anota algo, um pequeno modelo de aprendizado de máquina incluído no app decide se aquilo parece uma tarefa, um item de compras, uma entrada de diário ou uma nota, e organiza os itens de compras por seção do mercado. Os modelos rodam no dispositivo. Seu texto não é enviado a lugar nenhum para isso. Para um idioma para o qual não incluímos modelo, o app pergunta à [Apple Intelligence](https://www.apple.com/legal/privacy/data/en/intelligence-engine/) no dispositivo quando ela está disponível, e caso contrário não faz nada.
- **Busca.** O índice de busca do Popt é criado no seu dispositivo a partir do seu conteúdo descriptografado e nunca sai dele. Se você ativar a Siri e o Spotlight para o Popt, o índice da própria Apple no dispositivo recebe as tarefas, listas e notas que você escolher. Esse índice fica no dispositivo e é coberto pela [política da Siri da Apple](https://www.apple.com/legal/privacy/data/en/ask-siri-dictation/).
- **Verificação de fotos.** Em dispositivos onde o Aviso de Conteúdo Sensível ou a Segurança na Comunicação da Apple estão ativados, o Popt pede ao iOS que verifique, no dispositivo, cada foto que mostra em busca de nudez. As fotos sinalizadas são desfocadas. As fotos não são enviadas a lugar nenhum para essa verificação, e nunca ficamos sabendo do resultado.
- **Faixa etária.** Se você usar um recurso com restrição de idade, o Popt pergunta ao iOS em qual faixa etária você se enquadra (menos de 13, 13 a 15, 16 a 17 ou 18 ou mais). O Popt nunca vê uma data de nascimento. A resposta é guardada com seus ajustes criptografados, então não conseguimos lê-la no nosso banco de dados. O único lugar em que ela viaja em texto legível é a busca de Adicionar à biblioteca: a faixa aproximada (menos de 13, 13 a 15, 16 a 17, 18 ou mais) acompanha a busca para que os resultados sejam adequados à idade, sem a sua conta vinculada.
- **Localização.** Anexar um lugar a uma entrada usa a localização do seu dispositivo só quando você escolhe, e só se você tiver permitido isso no iOS. As coordenadas são criptografadas como qualquer outro conteúdo. Converter as coordenadas em endereço é uma requisição do seu dispositivo ao Apple Maps, sob as políticas de [Serviços de Localização](https://www.apple.com/legal/privacy/data/en/location-services/) e do [Apple Maps](https://www.apple.com/legal/privacy/data/en/apple-maps/) da Apple. Isso nunca passa pelos nossos servidores.
- **Lembretes.** Os alertas de lembrete de tarefas com data são agendados localmente pelo app, não por um servidor.

## Recursos sociais

O Popt não tem diretório público de perfis: ninguém pode encontrar você ou ver nada seu sem um convite direto. Tudo o que você compartilha continua criptografado de ponta a ponta, e as pessoas com quem você compartilha só podem ler o que você compartilhou. Nossos servidores veem os identificadores das contas envolvidas, nunca o conteúdo.

### Convites

Um convite é um link. A mensagem e o item da biblioteca opcionais dentro dele são criptografados no seu dispositivo com uma chave que viaja no próprio link, para que o conteúdo do convite não fique armazenado em texto legível no nosso servidor, mas os convites continuem podendo ser pré-visualizados por quem tiver o link completo. Aceitar um convite conecta os dois identificadores de conta como amigos e troca as chaves sobre as quais o compartilhamento futuro é construído.

### Publicações

Uma publicação é criptografada para os amigos que você escolheu ao publicá-la, e cada comentário é criptografado para as pessoas que estão na publicação naquele momento.
- Só o usuário que publicou pode adicionar ou remover participantes
- Novos participantes não veem os comentários anteriores
- Participantes removidos não conseguem ver os comentários mais novos, mas mantêm acesso à publicação e a todos os comentários que podiam ver quando foram removidos

### Mensagens

Cada lado de uma conversa é dono da própria metade: suas mensagens são criptografadas com uma chave que só vocês dois têm, e a outra pessoa não pode editá-las nem apagá-las. Apagar uma mensagem sua a remove para os dois. Nossos servidores veem que dois identificadores de conta trocam mensagens criptografadas, e quando.

### Listas, projetos e notas compartilhados

O conteúdo colaborativo é criptografado com uma chave compartilhada por todos que fazem parte dele, e cada membro pode ler ou editar conforme a função que você deu a ele. Quando você remove alguém, o conteúdo é criptografado de novo com uma nova chave e retirado dos dispositivos dessa pessoa na próxima sincronização. O que ela escreveu enquanto era membro continua na lista, sob a sua propriedade.

### Denúncias de abuso

A denúncia é o único caso em que conteúdo chega até nós em forma legível. Quando você denuncia um perfil, uma publicação ou uma mensagem, a denúncia carrega o conteúdo denunciado, suas fotos e, no caso de uma mensagem, as poucas mensagens ao redor para dar contexto, além de uma observação opcional. O conteúdo denunciado é exibido antes do envio da denúncia, para que você saiba exatamente o que está enviando. A denúncia é então criptografada no seu dispositivo antes de ser enviada para nós, de modo que só nossa equipe de análise possa abri-la. A conta denunciada não é informada da sua denúncia, mas pode ser suspensa ou banida por completo do uso dos nossos serviços.

## Apagar e manter dados

**Apagar conteúdo.** Tudo o que você apaga vai para Apagados recentemente por 30 dias, onde você pode restaurá-lo ou apagá-lo definitivamente na hora. Depois de 30 dias, nossos servidores o apagam em definitivo. Uma foto ou arquivo é apagado do armazenamento assim que o último item que aponta para ele desaparece. O conteúdo compartilhado com outras pessoas também vive nos dispositivos delas: apagar a sua cópia não apaga a delas.

**Apagar sua conta.** Abra Minha conta, escolha Apagar conta e digite a frase de confirmação. Em até 7 dias, apagamos seu login, seu perfil, suas chaves, seu conteúdo e arquivos criptografados, seus tokens de push e seus ajustes de notificação. Listas, notas e projetos compartilhados que pertencem a você são apagados para todos que fazem parte deles, assim como suas publicações com todos os comentários, seus comentários nas publicações de outras pessoas e suas mensagens. O que você adicionou a listas, notas e projetos dos seus amigos continua lá. Seus amigos passam então a ver “Conta apagada” no lugar do seu nome. Tudo o que você adicionar entre o pedido e a exclusão também é apagado, e nada pode ser recuperado depois. Apagar sua conta não cancela uma assinatura do Popt Pro: cancele-a nos ajustes de assinaturas da sua Conta Apple. Se você não tiver mais nenhum dispositivo com sessão iniciada, envie um e-mail para support@popt.com a partir do endereço com o qual se cadastrou e apagaremos a conta para você.

Alguns dados precisam ser mantidos por mais tempo para cumprir nossas obrigações legais:
- Os registros de assinatura que a Apple nos obriga a manter para fins contábeis são mantidos pelo tempo exigido por lei.
- As denúncias de abuso são mantidas enquanto precisarmos delas para agir sobre a denúncia e responder pela nossa decisão, mesmo depois que a conta denunciada deixa de existir.

**Encerrar a sessão** apaga seu conteúdo do dispositivo: o banco de dados, os caches de fotos e arquivos, os cookies e logins do navegador, o índice do Spotlight e seus ajustes. Se você tiver ativado as Chaves do iCloud no dispositivo em que iniciou a sessão no Popt, o código de recuperação permanece nas suas chaves para que você possa voltar a iniciar a sessão no Popt com facilidade, em qualquer dispositivo em que esteja conectado com o mesmo ID Apple.

**Todo o resto dura pouco.** Os registros de entrega de notificações são apagados depois de 31 dias; códigos de início de sessão, links de convite e contadores de limite de requisições são apagados quando expiram.

## Seus direitos

Onde quer que você more, você tem direitos sobre seus dados, e damos a todos o conjunto completo de direitos do RGPD. A maioria deles você pode exercer por conta própria dentro do app, e é assim que preferimos, porque não conseguimos ler seu conteúdo e não deveríamos precisar.

- **Acesso e portabilidade.** Exporte tudo em Minha conta. A exportação é uma pasta de arquivos Markdown simples e suas fotos, legível por qualquer editor de texto e pelo Obsidian. Ela cobre seu próprio conteúdo e o que outras pessoas compartilharam com você. O conteúdo em um cofre secreto é exportado movendo-o primeiro para o Início, de dentro do cofre.
- **Correção.** Edite qualquer coisa no app. Seu nome de perfil, seu status e seu avatar são seus para mudar a qualquer momento.
- **Exclusão.** Apague conteúdo, ou sua conta inteira, como descrito acima.
- **Oposição e restrição.** Não fazemos perfilamento, publicidade nem decisões automatizadas sobre você, então não há a que se opor nesse sentido. Se você acredita que guardamos algo que não deveríamos, escreva para nós.
- **Retirada do consentimento.** Localização, notificações, acesso às fotos e faixa etária são permissões do iOS que você pode retirar nos Ajustes a qualquer momento. O app continua funcionando sem elas.
- **Reclamação.** Você pode reclamar ao Comissário Federal de Proteção de Dados e Informação da Suíça (FDPIC, edoeb.admin.ch) ou à autoridade de proteção de dados do seu próprio país. Preferimos que você escreva para nós primeiro, mas não é obrigatório.

Para qualquer coisa que você não consiga fazer no app, envie um e-mail para **support@popt.com**. Como não conseguimos ver seu conteúdo, podemos pedir que você prove que controla a conta, por exemplo escrevendo a partir do endereço de e-mail com o qual se cadastrou.

**Onde seus dados estão.** Nossos servidores e nosso armazenamento ficam nos Estados Unidos, como descrito em [Serviços aos quais o app se conecta](#serviços-aos-quais-o-app-se-conecta). As transferências para fora da Suíça e da UE são cobertas pelas cláusulas contratuais padrão da UE com cada provedor, e pela própria criptografia: o que sai é conteúdo que não conseguimos ler.

## Crianças e idade

O Popt é classificado como 13+ na App Store, e os pais podem aprová-lo para uma criança mais nova pelo Tempo de Uso. O único dado pessoal envolvido nisso é a **faixa etária**, e é assim que lidamos com ela.

Nunca pedimos data de nascimento. Quando alguém usa um recurso com restrição de idade pela primeira vez, o Popt pergunta ao iOS em qual faixa etária essa pessoa se enquadra (menos de 13, 13 a 15, 16 a 17 ou 18 ou mais) por meio da API Declared Age Range da Apple, que os pais configuram nos ajustes de Família. A resposta é guardada com seus ajustes criptografados, onde não conseguimos lê-la. O único lugar em que a faixa viaja em texto legível é a busca de Adicionar à biblioteca, para que os resultados sejam adequados à idade, e ela não é vinculada à sua conta.

O que cada faixa etária desbloqueia, como funciona a aprovação dos pais para novos amigos e como as fotos sinalizadas são tratadas está explicado na nossa página de segurança de conteúdo: [popt.com/content-safety](https://popt.com/content-safety). Não coletamos mais nada sobre menores.

## Verifique por conta própria

Você não deveria ter que acreditar na nossa palavra sobre nada disso. Publicamos o **veri-popt**, um conjunto de ferramentas e documentação para verificar a criptografia do Popt: [github.com/SkileSA/veri-popt](https://github.com/SkileSA/veri-popt).

## Alterações nesta política

Quando mudamos o que o app coleta ou com quem ele se comunica, atualizamos esta política primeiro e o app depois. A data no topo é a data da última alteração, e o histórico completo de versões é público no nosso repositório de documentos legais no GitHub, junto com nossos Termos de Serviço: [github.com/SkileSA/popt-legal](https://github.com/SkileSA/popt-legal). Para uma alteração que reduza sua privacidade, avisaremos você por e-mail antes de ela entrar em vigor.
