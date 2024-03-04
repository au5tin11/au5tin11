import pygame
import sys

# Initialize Pygame
pygame.init()

# Set up screen dimensions
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Simple 2D Game")

# Set up colors
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)

# Set up player properties
player_width = 50
player_height = 50
player_x = (SCREEN_WIDTH - player_width) // 2
player_y = (SCREEN_HEIGHT - player_height) // 2
player_speed = 5

# Main game loop
running = True
while running:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Get keys pressed
    keys = pygame.key.get_pressed()

    # Move player
    if keys[pygame.K_LEFT]:
        player_x -= player_speed
    if keys[pygame.K_RIGHT]:
        player_x += player_speed
    if keys[pygame.K_UP]:
        player_y -= player_speed
    if keys[pygame.K_DOWN]:
        player_y += player_speed

    # Boundary checking for player
    if player_x < 0:
        player_x = 0
    elif player_x > SCREEN_WIDTH - player_width:
        player_x = SCREEN_WIDTH - player_width
    if player_y < 0:
        player_y = 0
    elif player_y > SCREEN_HEIGHT - player_height:
        player_y = SCREEN_HEIGHT - player_height

    # Fill the screen with black
    screen.fill(BLACK)

    # Draw the player
    pygame.draw.rect(screen, WHITE, (player_x, player_y, player_width, player_height))

    # Update the display
    pygame.display.flip()

    # Cap the frame rate
    pygame.time.Clock().tick(60)

# Quit Pygame
pygame.quit()
sys.exit()
