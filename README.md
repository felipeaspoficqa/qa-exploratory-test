# qa-exploratory-test
Teste técnico para vaga de QA utilizando testes exploratórios nas telas de login e cadastro.

## Abordagem de Testes

Como não foram fornecidos requisitos funcionais detalhados, foram realizados **Testes Exploratórios**, considerando comportamentos esperados comuns em sistemas de autenticação.

Foram analisados os seguintes fluxos:

- Cadastro de usuário
- Login de usuário

Durante os testes foram observados aspectos relacionados a:

- Validação de campos
- Consistência do sistema
- Experiência do usuário (UX)
- Regras básicas de autenticação

---

# Bugs Encontrados

## Bug 1 — Cadastro permitido com campos vazios

**Descrição**  
O sistema permite que uma conta seja criada mesmo quando todos os campos do formulário de cadastro estão vazios.

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Deixar todos os campos vazios  
3. Clicar no botão de cadastro  

**Resultado atual**  
O sistema cria a conta mesmo sem nenhuma informação preenchida.

**Resultado esperado**  
O sistema deve impedir o cadastro e informar que os campos obrigatórios precisam ser preenchidos.

**Severidade**  
Crítico

**Prioridade**  
Alta

---

## Bug 2 — Cadastro permite múltiplas contas com o mesmo email

**Descrição**  
O sistema permite criar mais de uma conta utilizando o mesmo endereço de email.

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Criar uma conta utilizando um email válido  
3. Tentar criar outra conta utilizando o mesmo email  

**Resultado atual**  
O sistema permite a criação de múltiplas contas com o mesmo email.

**Resultado esperado**  
O sistema deve impedir o cadastro e informar que o email já está em uso.

**Severidade**  
Alta

**Prioridade**  
Alta

---

## Bug 3 — Campos do cadastro aceitam qualquer tipo de caractere

**Descrição**  
Os campos do formulário de cadastro aceitam qualquer tipo de caractere sem validação adequada.

Exemplos observados:

- Campo **Nome** aceita números e caracteres especiais  
- Campo **Telefone** aceita letras  
- Campo **Email** aceita formatos inválidos  

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Inserir caracteres inválidos nos campos  
3. Tentar concluir o cadastro  

**Resultado atual**  
O sistema aceita os valores inseridos sem realizar validação.

**Resultado esperado**  
O sistema deve validar o tipo de dado adequado para cada campo.

**Severidade**  
Alta

**Prioridade**  
Alta

---

## Bug 4 — Campos do cadastro não possuem limite mínimo ou máximo

**Descrição**  
Os campos do formulário não possuem restrições de tamanho mínimo ou máximo para os dados inseridos.

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Inserir uma quantidade muito grande de caracteres em qualquer campo  
3. Tentar concluir o cadastro  

**Resultado atual**  
O sistema aceita qualquer tamanho de entrada.

**Resultado esperado**  
O sistema deve possuir limites definidos para evitar entradas excessivas ou inválidas.

**Severidade**  
Alta

**Prioridade**  
Média

---

## Bug 5 — Campos do cadastro visualmente desalinhados

**Descrição**  
Os campos do formulário de cadastro apresentam desalinhamento visual, o que pode prejudicar a experiência do usuário.

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Observar a disposição e alinhamento dos campos  

**Resultado atual**  
Os campos apresentam desalinhamento visual.

**Resultado esperado**  
Os campos devem estar organizados e alinhados adequadamente na interface.

**Severidade**  
Baixa

**Prioridade**  
Baixa

---

## Bug 6 — Login permitido com campos vazios

**Descrição**  
O sistema permite que o usuário realize login mesmo deixando os campos de **email** e **senha** vazios.

**Passos para reproduzir**

1. Acessar a tela de login  
2. Deixar os campos de email e senha vazios  
3. Clicar no botão de login  

**Resultado atual**  
O sistema permite o login sem credenciais.

**Resultado esperado**  
O sistema deve impedir o login e informar que os campos precisam ser preenchidos.

**Severidade**  
Crítico

**Prioridade**  
Alta

---

## Bug 7 — Mensagem de erro exibida após login bem sucedido

**Descrição**  
Ao realizar login com credenciais válidas, o sistema redireciona o usuário para a página de sucesso, porém também exibe uma mensagem de **erro inesperado**.

**Passos para reproduzir**

1. Criar uma conta válida  
2. Acessar a tela de login  
3. Inserir email e senha corretos  
4. Realizar login  

**Resultado atual**  
O usuário é redirecionado para a página de sucesso, mas uma mensagem de erro inesperado também é exibida.

**Resultado esperado**  
O sistema deve exibir apenas a confirmação de login bem-sucedido.

**Severidade**  
Baixa

**Prioridade**  
Alta

---

## Bug 8 — Regra de senha exibida mas não validada

**Descrição**  
Existe uma mensagem informando que a senha deve conter no mínimo 8 caracteres e 1 caractere especial, porém essa regra não é validada pelo sistema.

**Passos para reproduzir**

1. Acessar a tela de cadastro  
2. Inserir uma senha que não atende aos requisitos informados  
3. Concluir o cadastro  

**Resultado atual**  
O sistema aceita qualquer senha.

**Resultado esperado**  
O sistema deve validar os requisitos informados e impedir o cadastro caso não sejam atendidos.

**Severidade**  
Crítico

**Prioridade**  
Alta

---

# Priorização de Correções dos Bugs

## Quais 2 bugs eu corrigiria primeiro e por quê?

### 1 — Login permitido com campos vazios

Esse bug impacta diretamente o fluxo de autenticação e representa um problema crítico de segurança e lógica do sistema.
Permitir login sem credenciais válidas pode comprometer a integridade da aplicação e permitir acessos indevidos.
Por esse motivo, ele deve ser tratado com prioridade máxima.

### 2 — Cadastro permitido com campos vazios

Esse problema compromete a qualidade dos dados armazenados no sistema e pode gerar múltiplas contas inválidas.
Além disso, pode afetar diretamente funcionalidades futuras que dependem de informações válidas do usuário.
Por isso, deve ser corrigido rapidamente para garantir a integridade dos dados.

---

# Sugestões de Melhoria

### 1 — Implementar botão de visualização de senha

Adicionar um botão de visualização de senha nos campos de senha das telas de login e cadastro.
Isso ajuda o usuário a verificar a senha digitada.

### 2 — Melhorar validação dos campos

Implementar validações específicas para cada campo do formulário.

### 3 — Definir limites mínimos e máximos de caracteres

Estabelecer limites de tamanho para os campos do formulário para evitar entradas inválidas ou muito longas.

### 4 — Adicionar mensagens de erro

Apresentar mensagens de erro claras e específicas para orientar o usuário sobre o que precisa ser corrigido no formulário.

---

## Pontos Positivos Observados

Durante a análise também observei alguns aspectos positivos nas telas.

- O fluxo de navegação entre cadastro, login e tela de sucesso está funcional.
- As regras de senha estão descritas na interface, o que ajuda o usuário na hora de preencher o campo.
- O sistema exibe uma mensagem de "conta não encontrada" quando o usuário tenta logar com um e-mail ainda não cadastrado.

