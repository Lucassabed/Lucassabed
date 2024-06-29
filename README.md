- 👋 Hi, I’m @Lucassabed
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Lucassabed/Lucassabed is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changesimport pygame
from pygame.locals import *

# Inicialização do Pygame
pygame.init()

# Configurações da tela
largura, altura = 800, 600
tela = pygame.display.set_mode((largura, altura), DOUBLEBUF | OPENGL)

# Configurações de OpenGL básicas
glClearColor(0.5, 0.5, 0.5, 1.0)  # Cor de fundo cinza claro

# Variáveis para controle de movimento da bola
x, y = 0, 0  # Posição inicial da bola
vx, vy = 0.01, 0.01  # Velocidade inicial da bola

# Função para desenhar uma bola
def desenha_bola(x, y):
    glBegin(GL_QUADS)
    glColor3f(1.0, 0.0, 0.0)  # Cor vermelha
    glVertex3f(x - 0.1, y - 0.1, 0.0)
    glVertex3f(x + 0.1, y - 0.1, 0.0)
    glVertex3f(x + 0.1, y + 0.1, 0.0)
    glVertex3f(x - 0.1, y + 0.1, 0.0)
    glEnd()

# Loop principal do jogo
while True:
    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            quit()

    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)

    # Atualizar posição da bola
    x += vx
    y += vy

    # Verificar colisão com bordos da tela
    if x + 0.1 > 1 or x - 0.1 < -1:
        vx = -vx
    if y + 0.1 > 1 or y - 0.1 < -1:
        vy = -vy

    # Desenhar a cena
    desenha_bola(x, y)

    pygame.display.flip()
    pygame.time.wait(10)
    
