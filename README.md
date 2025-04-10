Explicação do Código e Resultado:

Ó, esse código aqui é pra resolver um problema que nem um drone subindo uma montanha pra achar o lugar mais alto, sabe? A gente tem uma funçãozinha que é tipo uma montanha com vários altos e baixos, e o nome dela é f(x)=sin⁡(5x)⋅(1−tanh⁡(x2)) f(x) = \sin(5x) \cdot (1 - \tanh(x^2)) f(x)=sin(5x)⋅(1−tanh(x2)). Parece complicadão, né? Mas calma, é só um jeito de dizer que a montanha tem uns picos e uns vales, e a gente quer achar o pico mais alto entre x=−2 x = -2 x=−2 e x=2 x = 2 x=2.

O que o código faz, tipo, de verdade?

A gente usa um treco chamado Simulated Annealing, que é tipo um drone bobo que vai andando pela montanha pra achar o lugar mais alto. Ele não sabe onde tá o pico, então ele vai dando uns passinhos pra lá e pra cá e vendo se tá subindo ou descendo. No final, ele fala: "Achei um lugar bem alto aqui, ó!"

Como o código funciona? Passo a passo, bem devagarinho:

A função f(x) f(x) f(x):
A gente faz uma função que é essa f(x)=sin⁡(5x)⋅(1−tanh⁡(x2)) f(x) = \sin(5x) \cdot (1 - \tanh(x^2)) f(x)=sin(5x)⋅(1−tanh(x2)).

O sin⁡(5x) \sin(5x) sin(5x) é tipo uma onda que sobe e desce bem rápido, que nem uma montanha com vários picos.
O 1−tanh⁡(x2) 1 - \tanh(x^2) 1−tanh(x2) é um negócio que faz os picos ficarem menores quanto mais longe do zero o x x x for. Então, no meio (x=0 x = 0 x=0), os picos são altos, e nas pontas (x=2 x = 2 x=2 ou x=−2 x = -2 x=−2), eles ficam bem baixinhos.
O Simulated Annealing (o drone bobo):

A gente começa jogando o drone em qualquer lugar da montanha, tipo, um x x x aleatório entre -2 e 2. "Vai lá, drone, se vira!"
Aí, o drone dá um passinho pra esquerda ou pra direita. Esse passinho é um número bem pequeno, tipo entre -0.1 e 0.1 (a gente chama de ϵ \epsilon ϵ). Então, o novo lugar é xnovo=x+ϵ x_{\text{novo}} = x + \epsilon xnovo​=x+ϵ.
O drone olha: "Tô mais alto ou mais baixo agora?" Ele calcula f(xnovo) f(x_{\text{novo}}) f(xnovo​), que é a altura no lugar novo.
Como a gente quer o lugar mais alto, o drone usa um truque: ele finge que tá procurando o menor valor de −f(x) -f(x) −f(x). Se −f(xnovo) -f(x_{\text{novo}}) −f(xnovo​) for menor que −f(x) -f(x) −f(x), significa que f(xnovo) f(x_{\text{novo}}) f(xnovo​) é maior, ou seja, ele subiu! Aí ele vai pra lá na hora.
Mas se o lugar novo for mais baixo, o drone fala: "Hmm, será que eu desço mesmo assim?" Ele tem uma chance de descer, que depende de uma coisa chamada "temperatura" (T T T). No começo, a temperatura é alta (T=1.0 T = 1.0 T=1.0), então o drone é mais aventureiro e desce mais fácil. Ele usa uma fórmula esquisita, e−Δ/T e^{-\Delta/T} e−Δ/T, pra decidir se desce ou não.
A temperatura vai caindo (a gente multiplica por 0.95 a cada rodada), então o drone fica mais "sério" e prefere só subir no final.
A gente também guarda todos os lugares que o drone passou pra fazer um desenho depois.
Os números que a gente usa:

Temperatura começa em 1.0.
A gente diminui ela com α=0.95 \alpha = 0.95 α=0.95.
A cada temperatura, o drone tenta 100 passinhos antes de esfriar mais.
Os desenhos (gráficos):

Primeiro desenho: Mostra a montanha inteira (a função f(x) f(x) f(x)) entre x=−2 x = -2 x=−2 e x=2 x = 2 x=2. A gente também marca com um pontinho vermelho o lugar mais alto que o drone achou.
Segundo desenho: Mostra o caminho que o drone fez. Tipo, "Olha como eu andei pra lá e pra cá até achar o pico!" É uma linha que mostra os x x x que ele visitou.

O que aparece no final?

O drone fala: "Achei um lugar alto aqui!" Ele te dá o x x x e a altura f(x) f(x) f(x) desse lugar. Tipo: "Melhor lugar: x=0.31 x = 0.31 x=0.31, altura f(x)=0.93 f(x) = 0.93 f(x)=0.93". Mas como o drone é meio bobo e usa números aleatórios, toda vez que você roda o código, ele pode achar um x x x um pouquinho diferente.
Você também vê os dois desenhos:

Um com a montanha e o pico que o drone achou (em vermelho).
Outro com o caminho que o drone percorreu (tipo, "Olha como eu fui andando!").
Na verdade, os picos mais altos da montanha tão perto de x=0.3 x = 0.3 x=0.3 ou x=−0.3 x = -0.3 x=−0.3. O drone geralmente acha um desses, mas como ele é meio aleatório, pode variar um tiquinho.

Pra que serve isso?

É tipo um jeito de achar o lugar mais alto de uma montanha sem saber onde ele tá. O drone vai andando, às vezes desce pra explorar, mas no final ele acha um pico bem alto. E os desenhos ajudam a ver como ele trabalhou pra chegar lá!
