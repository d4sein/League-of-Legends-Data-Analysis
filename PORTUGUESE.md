## Visão geral

O aspecto mais notável de League of Legends é a sua natureza competitiva. As pessoas querem melhorar e subir de ranking, mas não é tão fácil achar as estratégias corretas; ou os melhores itens contra campeões ou composições específicas.  

Com isso em mente, a Análise de Dados pode nos ajudar a entender o valor de certos objetivos, e o quão importante é fazer **"counter items"** quando contra campeões como Nasus e Vladimir.  

**counter items:** itens com o objetivo de reduzir a eficiência do time inimigo, em algum ponto específico.  

*Obs: Alguns termos permanecerão em Inglês para manter a coesão das frases.*

## Abordagem

A ideia foi usar a API da Riot e reunir jogos de todas as plataformas e rankings, totalizando aproxidamente 180.000, e então refinar todos esses dados para analisar depois. Tudo seria salvo em um arquivo mongoDB, por ser a maneira mais simples.  

Escrevi dois scripts pra isso e eles podem ser encontrados nesse repositório.  

Também, os dados foram coletados durante o patch 10.9.  

## Resultados

#### Arauto
Subestimado, o primeiro Arauto aumenta a taxa de vitória para 63%, e em casos onde o time captura ambos, as chances aumentam para 74%. Claro, não foi considerado o quão à frente eles estavam, mas mostra que é um objetivo importante, de qualquer forma.  

#### Seleção de itens
Seleção de itens, ou **"itemization"**, não é apenas uma maneira de aumentar suas forças, mas também um ataque pra enfraquecer o time inimigo. Sempre tem um aliado pra marcar *Morellonomicon* no chat quando o Vladimir pega uma **kill**, e isso tem um motivo, a taxa de vitória contra o Vlad é de 50%, mas quando pegamos apenas jogos onde nenhum item de corta-cura foi feito, ela cai pra 24%, e é ainda pior pro Nasus, com uma taxa de vitória de apenas 20%.  

Isso considerando apenas os itens, então tenha em mente que habilidades como a **ultimate** da Katarina ou *Incendiar* também servem o mesmo propósito.  

**ultimate:** habilidade especial de um campeão.  

Além de **counter items**, há maneiras de maximizar as capacidades do seu campeão, como *Velocidade de Ataque* pro Jax, ou *Penetração Mágica* pra Elise. Essas opções funcionam bem pra eles porque o Jax é um champ baseado em ataque básico, o que significa que seu dano vem majoritariamente de ataques básicos, e pra Elise, ela é um champ com muito dano no começo do jogo, mas que não escala bem com **AP (Ability Power / Poder de Abilidade)**, então ter essa penetração é mais eficiente.  

Alguns campeões têm uma maior liberdade na escolha dos itens, outros não, que é o caso do Fiddlesticks. Fiddle tem uma **ultimate** poderosa para as lutas de equipe, mas é inútil se você morrer logo após usá-la, então fazer a *Ampulheta de Zhonya* é quase que obrigação, já que o item te permite usar a habilidade e permanecer em segurança até que seu time acabe com o time inimigo.  

Em questão de números, Fiddlesticks tem uma taxa de vitória de 51% globalmente, mas quando isolamos os jogos onde a *Ampulheta de Zhonya* não foi feita, ela cai pra 42%, solidificando a tese.  

Algumas informações extra que encontrei é que Trundle **Jungle** de *Encantamento: Guerreiro* tem uma taxa de vitória de 49%, 4% menor se comparada com Trundle Jungle de *Encantamento: Titã Ardente*, com 53%. Guerreiro é provavelmente uma escolha situacional para carregar o jogo, enquanto que Titã Ardente é uma opção mais segura. Isso também reforça o fato de que o Trundle escala melhor com vida do que **AD (Attack Damage / Dano de Ataque)**.  

E finalmente, enquanto procurava por correlações entre campeões com identidades parecidas, percebi que todos esses champs: Jax, Renekton, Vayne, Kalista e Twitch, têm a *Espada do Rei Destruído* nos seus top 5 itens feitos, mostrando que o item é realmente forte (um pouco até demais) para campeões baseados em ataque básico. Algo semelhante acontece para magos, todos eles fazem *Sapatos do Feiticeiro*, o que é.. não muito surpreendente, mas ajuda a reforçar o que já sabemos.  

#### Runas
Esse tópico é um pouco problemático de analisar, já que as runas dependem muito da composição do time e da estratégia adotada, você pode jogar com o mesmo campeão usando runas diferentes baseado nas circunstâncias. Pra resolver esse problema, podemos filtrar jogos com um conjunto de parâmetros, o que nos permite ter resultados mais plausíveis.  

Também vou me abster de explicar cada runa ou **perk**, pois alguns são bem extensos.  

Por exemplo, o Kayn tem uma taxa de vitória de 56% de *Conquistador* + *Cutelo Negro*, dessa forma podemos assumir que ele provavelmente está jogando de Kayn Vermelho, caso contrário, se apenas considerando as runas, teríamos um resultado distorcido, com 49%. Além disso, Kayn com *Eletrocutar* + *Botas da Mobilidade* tem uma taxa de vitória de 53%, 1% maior que o Kayn de *Colheita Sombria* + *Botas da Mobilidade*, com 52%. Isso é esperado, já que o Kayn Vermelho é relativamente fácil de jogar, e *Eletrocutar* é uma runa mais simples, enquanto que *Colheita Sombria* depende de conhecimento de jogo pra ser eficiente.  

Outra **"build"** interessante que talvez surpreenda é Kha'Zix de *Conquistador* + *Cutelo Negro* em situações onde o time inimigo é composto por muitos lutadores ou tanques. Pra conseguir esse resultado eu filtrei jogos com três parâmetros: primeiro e mais óbvio, somente Conquistador como runa primária; segundo, somente jogos onde o *Cutelo Negro* foi feito, já que é um item essencial pra **build**; terceiro, o time inimigo deve ter ao menos dois campeões de uma lista, onde eu inclui champs como Jax, Darius, Garen, Aatrox, Hecarim, Kled, etc. Surpreendemente, Kha'Zix tem uma boa performance nesses casos, com uma taxa de vitória de 52%.  

**build:**: conjunto de itens que juntos desempenham um papel específico.  

Como últimas observações nesse tópico, podemos dar uma olhada no quão eficiente alguns **perks** são de modo geral, e se eles sinergizam bem com certos campeões.  

*Caça Voraz* tem uma média de 2% de cura do dano inflingido, 0.5% acima dos status base, porém 7 vezes menor que o limite, de 14%. Melhora um pouco pra Elise e Kha'Zix, com 3% e 3.2%, respectivamente.  

*Caminhar Sobre as Águas* é um dos **perks** favoritos dos **Junglers**, com 17.5% de tempo ativo pra essa rota, e 16% no geral. Definitivamente vale a pena dar uma olhada.  

## Conclusão

Essa análise é uma tentativa de aumentar o entendimento dos fundamentos do jogo de modo a maximizar as taxas de vitória. Selecionar um campeão, fazer um item, iniciar um objetivo, todas essas coisas devem ser feitas com um plano em mente.  
