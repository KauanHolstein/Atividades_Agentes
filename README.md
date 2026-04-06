Robo de Navegação Autônoma 

A ideia desse projeto é simples: colocar um robozinho numa grade e ver até onde ele consegue chegar. O que começa como um passeio aleatório vai evoluindo, etapa por etapa, até o robô ser capaz de planejar rotas inteligentes desviando de obstáculos e minimizando custos — tudo isso com uma janela gráfica pra você acompanhar em tempo real.

 Etapa 1 — Dando os primeiros passos

Na primeira etapa (`RoboEtapaUm`), o robô aparece em algum lugar aleatório de uma grade 10×10 e começa a se mover sem nenhum critério — apenas escolhendo uma direção disponível ao acaso a cada 300ms. Sem memória, sem objetivo, sem estratégia. É quase como observar uma formiga desorientada, mas já dá pra entender o mecanismo básico de movimento e perceber quando o robô bate em alguma borda do mapa.

 Etapa 2 — Aprendendo a não pisar no mesmo lugar

A segunda etapa (`RoboEtapaDois`) torna o cenário mais interessante. O mapa agora tem obstáculos espalhados e o robô parte sempre do canto superior esquerdo. A grande diferença aqui é que ele passou a ter memória: sabe onde já esteve e prefere explorar território novo sempre que possível. Quando não há mais nenhuma célula nova ao alcance, ele para. Você consegue ver o rastro da exploração se formando aos poucos na tela, o que deixa bem visual o quanto do mapa foi coberto.

 Etapa 3 — Finalmente, um destino

Na terceira etapa (`RoboEtapaTres`), o robô ganha um objetivo concreto: chegar até a posição (7, 7). Antes de dar qualquer passo, ele calcula o caminho mais curto usando o algoritmo BFS (Busca em Largura) e depois simplesmente o segue, sem hesitação. O destino aparece em vermelho na grade e o caminho percorrido vai ficando colorido conforme o robô avança. É a primeira vez que ele age com planejamento de verdade.

 Etapa 4 — O terreno tem preço

A quarta etapa é onde as coisas ficam mais ricas. O mapa agora tem células com custos diferentes — algumas mais fáceis de atravessar, outras mais difíceis — e o robô precisa encontrar não apenas um caminho, mas o caminho mais barato. Para isso, entra em cena o algoritmo de Dijkstra.

Essa etapa vem em duas variações. Na primeira (`RoboEtapaQuatroV1`), o robô conhece o mapa inteiro desde o início e calcula a rota ótima antes de sair do lugar. Simples e eficiente. Na segunda variação (`RoboEtapaQuatroV2`), o desafio fica maior: o robô começa sem saber os custos reais do terreno — as células aparecem como `?` até ele chegar perto. Conforme explora, vai revelando o que há ao redor e, se perceber que o caminho que planejou não é mais o melhor, recalcula a rota na hora. É a variação mais próxima de como robôs reais lidam com ambientes desconhecidos.

Como Executar

Você vai precisar do Java JDK 8 ou superior instalado. Com ele em mãos, compile e execute assim:

```bash
javac Robo/*.java
java -cp Robo RoboEtapaUm
```

Troque `RoboEtapaUm` pelo nome da etapa que quiser rodar (`RoboEtapaDois`, `RoboEtapaTres`, `RoboEtapaQuatroV1` ou `RoboEtapaQuatroV2`). Cada uma abre sua própria janela com a simulação acontecendo ao vivo.
