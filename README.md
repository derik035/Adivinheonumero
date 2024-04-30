import random

NUM_MIN = 1
NUM_MAX = 10

def le_nome_jogador():
    nome = ''
    while len(nome) == 0:
        nome = input('Qual é o nome do jogador? ')
        print('Olá ' + nome + ', Vamos jogar!')
    return nome

def cpm_pensa_numero():
    num = random.randint(NUM_MIN, NUM_MAX)
    print('Pensei num número entre ' + str(NUM_MIN) + ' e ' + str(NUM_MAX))
    print('Adivinhe Qual...')
    return num

def jogador_tenta_adivinhar(nome, num_pensado):
    print('Digite 0 (zero) para terminar')
    tentativas = 1
    valendo = True
    while valendo == True:
        prompt = 'Tentativa ' + str(tentativas) + '. Digite um número: '
        entrada = input(prompt)
        try:
            num_advinhado = int(entrada)
            if num_advinhado == 0:
                valendo = False
                print(nome + ' desistiu')
                print('O número que eu tinha pensado era', num_pensado)
            elif num_pensado == num_advinhado:
                print('Acertou! Parabéns, ' + nome + '!!')
                valendo = False
            else:
                print('O número que eu pensei é', end=' ')
                if num_pensado > num_advinhado:
                    print('maior que', end=' ')
                else:
                    print('menor que', end=' ')
                print(num_advinhado)
                tentativas += 1
        except ValueError:
            print(nome + ', por favor, digite um número.')
            tentativas += 1

# Execução do jogo
nome_jogador = le_nome_jogador()
numero_pensado = cpm_pensa_numero()
jogador_tenta_adivinhar(nome_jogador, numero_pensado)
# Primeiro codigo do livro python games João Rotta
