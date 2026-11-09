# Locadora de Veículos

Projeto da disciplina de Programação Orientada a Objetos.

## Sobre o projeto

Sistema web para gerenciar uma locadora de veículos. O backend é escrito em TypeScript com programação orientada a objetos e concentra as regras de negócio. O frontend, também em TypeScript, conversa com o backend por uma API REST e permite cotar, reservar, retirar e devolver veículos, além de acompanhar a frota e os clientes.

## Principais regras de negócio

- **Disponibilidade:** um veículo não pode ter duas locações no mesmo período, nem ser alugado enquanto está em manutenção.
- **Cliente apto:** a idade mínima e a categoria da CNH dependem do tipo de veículo (moto exige CNH A, carro exige CNH B). A CNH precisa estar válida até a data de devolução, e cliente com pendência não pode alugar.
- **Preço:** a diária varia conforme a categoria do veículo, com adicionais opcionais (seguro, cadeirinha, condutor extra) e desconto para locações longas.
- **Devolução:** multa por atraso, cobrança dos quilômetros acima da franquia e taxa de reabastecimento se o tanque voltar com menos combustível do que saiu.
- **Ciclo de vida:** a locação passa por Reservada → Em andamento → Finalizada (ou Cancelada), e cada etapa só aceita as operações que fazem sentido nela. Cancelar em cima da hora gera multa.
- **Manutenção:** ao atingir a quilometragem de revisão, o veículo sai da frota disponível até a manutenção ser concluída.

## Como a POO entra no projeto (previsto)

- Classe abstrata `Veiculo` com subclasses por categoria (econômico, executivo, SUV, moto), cada uma com sua tarifa e suas exigências.
- Interfaces para regras de cobrança, descontos e repositórios, com implementações que podem ser trocadas.
- Estados da locação representados como classes (padrão State) e políticas de desconto como estratégias (padrão Strategy).
- Objetos de valor como `Dinheiro`, `Periodo` e `Cpf`, que validam os próprios dados.
- Testes automatizados cobrindo as regras de negócio acima.

## Tecnologias

- TypeScript no backend e no frontend
- Node.js + Express (API REST)
- React + Vite (interface)
- Vitest (testes automatizados)

## Equipe

- Nome do integrante
