# flapybird
pygame: Biblioteca para criação de jogos em Python.
os: Manipula caminhos de arquivos, útil para carregar as imagens do jogo.
random: Gera números aleatórios, usado para variar a altura dos canos.

TELA_LARGURA = 500
TELA_ALTURA = 800
Define as dimensões da janela do jogo.

Carregamento de Imagens e Fontes
As imagens do jogo são carregadas da pasta imgs, e a escala é ajustada para um tamanho maior:

Além disso, uma fonte é configurada para exibir a pontuação:pygame.font.init()
FONTE_PONTOS = pygame.font.SysFont('arial', 50)



. Classe Passaro
A classe Passaro controla o comportamento do pássaro no jogo.

Atributos principais:
IMGS: Lista de imagens que representam o pássaro.
ROTACAO_MAXIMA: Define o limite para a rotação ao subir.
VELOCIDADE_ROTACAO: Velocidade com que o ângulo do pássaro muda.
TEMPO_ANIMACAO: Controla a troca de imagens para animar o bater de asas.
Métodos principais:
__init__: Inicializa o pássaro com sua posição, velocidade e estado inicial.
pular: Faz o pássaro pular ao ajustar sua velocidade.
mover: Atualiza a posição do pássaro com base na gravidade e ajusta o ângulo de rotação.
desenhar: Alterna entre as imagens do pássaro para animar o movimento das asas.
get_mask: Retorna uma máscara para detectar colisões.


4. Classe Cano
A classe Cano gerencia o comportamento dos obstáculos no jogo.

Atributos principais:
DISTANCIA: Define a distância vertical entre os canos.
VELOCIDADE: Velocidade com que os canos se movem para a esquerda.
Métodos principais:
__init__: Inicializa os canos e define a posição inicial.
definir_altura: Configura a altura dos canos de forma aleatória.
mover: Move os canos para a esquerda.
desenhar: Desenha os canos na tela.
colidir: Detecta colisões entre o pássaro e os canos.



5. Classe Chao
A classe Chao cria o efeito visual de movimento contínuo no chão.

Atributos principais:
VELOCIDADE: Velocidade do movimento do chão.
LARGURA: Largura da imagem do chão.
IMAGEM: Representação visual do chão.
Métodos principais:
__init__: Define as posições iniciais das partes do chão.
mover: Move o chão para a esquerda e reinicia o ciclo quando necessário.
desenhar: Desenha o chão na tela.



6. Função desenhar_tela
Desenha todos os elementos do jogo na tela:
def desenhar_tela(tela, passaros, canos, chao, pontos):
    tela.blit(IMAGEM_BACKGROUND, (0, 0))
    for passaro in passaros:
        passaro.desenhar(tela)
    for cano in canos:
        cano.desenhar(tela)
    texto = FONTE_PONTOS.render(f"Pontuação: {pontos}", 1, (255, 255, 255))
    tela.blit(texto, (TELA_LARGURA - 10 - texto.get_width(), 10))
    chao.desenhar(tela)
    pygame.display.update()


7. Função Principal main
A função main organiza o loop principal do jogo:
