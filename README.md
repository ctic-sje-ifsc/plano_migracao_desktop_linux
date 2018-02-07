# Plano de migração e padronização de sistema operacional em _desktops_

Neste repositório estão descritas as diretrizes e ações principais do nosso __plano de migração e padronização de sistema operacional__ utilizado na área administrativa do IFSC câmpus São José.

Acreditamos que as informações a seguir foram a chave do sucesso do nosso caso e que podem ajudar outras instituições nessa (árdua) tarefa.

## Histórico
Iniciamos o processo em março de 2016 com um universo de 130 máquinas e levamos um ano para atingir 85% do total. Os 15% restantes são máquinas de setores onde não é possível a migração (aplicativos específicos), ou há dificuldades técnicas e mesmo resistência para a migração.

Principais motivações para a migração:

* Gerente de configuração com melhor compatibilidade - atualmente [puppet](https://github.com/ctic-sje-ifsc/gerenciamento_config_puppet).
* Maior facilidade de manutenção principalmente via CLI.
* Equipe de T.I. mais capacitada para o sistema operacional.
* Padronização do parque.
* Segurança.
* Melhor utilização dos recursos do hardware.
* Economia de recurso público em geral.
* A longo prazo, maior aceitação na implantação de estrutura com _thin client_ com SO Linux.

## Diretrizes que consideramos fundamentais

* __Equipe unida com o mesmo propósito e com conhecimento satisfatórios em Linux, capacitada para resolver rapidamente principais problemas__: toda a equipe conhece os propósitos e sabe as principais respostas quando consultados e questionados. Foi super importante o fato da equipe utilizar sempre preferencialmente Linux e ter familiaridade com a plataforma, não somente as versões para servidor, mas também _desktop_.

* __Gerente de configuração validado, operacional e eficiente__: um gerente de configuração, como o [puppet](https://github.com/ctic-sje-ifsc/gerenciamento_config_puppet), para poder aplicar configurações globalmente de forma rápida e eficaz. No decorrer da execução acontecem muitos problemas (ou necessidade de melhorias) que podem inviabilizar o plano se não forem corrigidos de forma rápida e transparente. Toda configuração é feita de forma centralizada(via gerente de configuração).

* __Sistema de clonagem de máquinas eficiente__: um gerente de clonagem de máquinas, como o [FogProject](https://fogproject.org/), para poder entregar a máquina ao usuário final o mais rápido possível.

* __Principais gestores cientes do plano e conhecendo as motivações__: a atual gestão do IFSC câmpus São José entende e apoia as ações.

* __Estudar previamente cada setor, quais aplicativos institucionais são utilizados e criar atalhos "transparentes" para acessos remotos__: é utilizada uma abordagem de acesso remoto  para alguns (poucos) aplicativos que só rodam no Microsoft Windows ([exemplo](https://github.com/ctic-sje-ifsc/gerenciamento_config_puppet/tree/master/environments/production/modules/remoto_ibsispes/manifests)). Instalamos esses em um servidor Windows centralizado habilitado para acesso remoto, e há atalhos na área de trabalho dos usuários finais que iniciam o programa remoto de forma transparente, dando a sensação que o está utilizando localmente.

* __Justificativa e necessidade. Deixar claro quando os "problemas" no são causados pelo novo sistema operacional__: existe jutificativa ou necessidade para a outra proposta? Procuramos mostrar para o usuário que vamos dar suporte a todas as necessidades institucionais dele. Também, é importante salientar aos usuários e gestores quando algum problema não é relacionado a migração em si - para evitar uma rejeição antecipada.

* __Máquinas com serial do Windows são instaladas com DualBoot porém Windows oculto no GRUB__: isso garante uma margem de segurança para casos extremos e pontuais, que em poucos casos foram necessárias liberações esporádicas (conversão de arquivo, exibição de mídia, entre outros).

## Passo a passo básico

1. Reuniões para nivelamento de propósitos e conhecimentos da equipe de TI.
1. Enviar email básico para todos avisando sobre a padronização e que enviarão emails individuais combinando datas.
1. Criar uma tabela (exemplo a seguir), com todas as máquinas e status, divididas por salas e respectivo usuário.
1. Definir setores menos críticos (aplicativos multiplataforma ou _online_ e usuários mais acessíveis) para serem feitos primeiramente.
1. Consultar o respectivo setor sobre todos os aplicativos institucionais utilizados(inclusive os pouco utilizados).
1. Verificar a possibilidade de utilização/migração dos respectivos aplicativos e criar os módulos de automatização do gerente de configuração e fazer testes.
1. Enviar email para um ou dois usuários por setor marcando um dia que será feito e que ele deve fazer o backup.
1. Devolver a máquina com o usuário presente e alinhar com o usuário o básico do sistema e dos aplicativos para o desempenho da sua atividade institucional.
1. Acompanhar de perto utilização/dificuldades/problemas do usuário e dar prioridade no atendimento desses. É muito importante essa priorização e rapidez e/ou empenho na solução dos possíveis problemas iniciais.
1. Quando validado com os usuários de teste formatar as máquinas dos outros usuários.
1. Dar sempre atendimento prioritário e atenção para possíveis dificuldades advindas da mudança.

Tabela da relação padronização das maquinas do Câmpus:

![planilha](docs/tabelaa.png)
