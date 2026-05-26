# Guia Prático — Importar a Máquina Virtual Ubuntu Server no Oracle VirtualBox 7.2

## Ambiente do Laboratório

- Sistema Operacional: Microsoft Windows 11
- Virtualizador: Oracle VirtualBox 7.2
- Máquina Física:
  - CPU: Intel i7-14700K
  - Memória RAM: 32 GB
  - SSD: 480 GB M.2
- Arquivo da Máquina Virtual:
  - `UbuntuServer-OnPremises.ova`
- Rede do Laboratório:
  - `10.24.82.0/24`
- Objetivo:
  - Importar a VM
  - Configurar rede em modo Bridge (Ponte)
  - Iniciar a VM
  - Validar acesso remoto via SSH

---

# 📥 Etapa 1 — Verificar o Arquivo da Máquina Virtual

1. Abra o **Explorador de Arquivos** do Windows.
2. Acesse a pasta:

```text
Downloads
```

3. Verifique se o arquivo abaixo está disponível:

```text
UbuntuServer-OnPremises.ova
```

---

# 🖥️ Etapa 2 — Abrir o Oracle VirtualBox

1. Clique no menu **Iniciar**.
2. Pesquise por:

```text
Oracle VirtualBox
```

3. Abra o programa.

---

# 📦 Etapa 3 — Importar a Máquina Virtual (.OVA)

1. No VirtualBox clique em:

```text
Arquivo → Importar Appliance
```

2. Clique no ícone da pasta 📁.
3. Navegue até:

```text
Downloads
```

4. Selecione o arquivo:

```text
UbuntuServer-OnPremises.ova
```

5. Clique em:

```text
Próximo
```

6. Na tela de configurações:
   - Verifique nome da VM
   - Verifique memória RAM
   - Verifique CPU

7. Clique em:

```text
Finalizar
```

⏳ Aguarde a importação da máquina virtual.

---

# ⚙️ Etapa 4 — Configurar Rede em Modo Bridge (Ponte)

## Objetivo

Permitir que a máquina virtual receba um IP da rede física do laboratório.

---

## Passos

1. Selecione a VM importada.
2. Clique em:

```text
Configurações
```

3. Acesse:

```text
Rede
```

4. Na opção **Adaptador 1**:

✅ Marque:

```text
Habilitar Placa de Rede
```

5. Em **Conectado a:** selecione:

```text
Placa em modo Bridge
```

6. Em **Nome**, escolha a placa de rede cabeada do laboratório.

Exemplo:

```text
Intel Ethernet
Realtek PCIe
Ethernet
```

⚠️ NÃO selecionar Wi-Fi.

---

## Configuração Recomendada

| Opção | Valor |
|---|---|
| Adaptador | Adaptador 1 |
| Modo | Bridge (Ponte) |
| Tipo de placa | Intel PRO/1000 MT Desktop |
| Cabo conectado | Marcado |

---

# 🌐 Etapa 5 — Iniciar a Máquina Virtual

1. Clique em:

```text
Iniciar
```

2. Aguarde o boot do Ubuntu Server.

---

# 🔐 Etapa 6 — Login no Ubuntu Server

Na tela de login:

1. Digite o usuário informado pelo professor.
2. Digite a senha informada pelo professor.

---

# 🌍 Etapa 7 — Verificar Endereço IP da Máquina Virtual

Após o login execute:

```bash
ip addr
```

ou

```bash
hostname -I
```

---

## Resultado Esperado

A máquina virtual deve receber um IP da rede:

```text
10.24.82.x
```

Exemplo:

```text
10.24.82.150
```

---

# 🔎 Etapa 8 — Testar Comunicação de Rede

Execute:

```bash
ping 10.24.82.1
```

ou

```bash
ping google.com
```

Se houver resposta, a rede está funcionando corretamente.

---

# 🔐 Etapa 9 — Validar Serviço SSH

Verifique se o SSH está ativo:

```bash
sudo systemctl status ssh
```

---

## Resultado Esperado

Deve aparecer:

```text
active (running)
```

---

# 💻 Etapa 10 — Testar Acesso Remoto via SSH

No Windows 11:

1. Abra o:

```text
PowerShell
```

2. Execute:

```powershell
ssh usuario@10.24.82.x
```

Exemplo:

```powershell
ssh aluno@10.24.82.150
```

3. Digite:

```text
yes
```

na primeira conexão.

4. Informe a senha do usuário.

---

# ✅ Resultado Final Esperado

Ao concluir a atividade:

- ✅ VM importada corretamente
- ✅ Ubuntu Server iniciado
- ✅ Rede em modo Bridge funcionando
- ✅ IP da rede 10.24.82.0/24 recebido
- ✅ Comunicação com a rede validada
- ✅ Acesso remoto SSH funcionando

---

# 🛠️ Comandos Utilizados

## Ver IP

```bash
hostname -I
```

## Ver Interfaces

```bash
ip addr
```

## Testar Rede

```bash
ping 8.8.8.8
```

## Verificar SSH

```bash
sudo systemctl status ssh
```

## Acessar via SSH

```powershell
ssh usuario@IP
```

---

# 📚 Tecnologias Utilizadas

- Oracle VirtualBox 7.2
- Ubuntu Server 22.04.4 LTS
- SSH (Secure Shell)
- Rede Bridge (Ponte)
- Microsoft Windows 11

---

# 👨‍🏫 Observação

Esta máquina virtual será utilizada durante as aulas práticas de Inteligência Artificial voltada a Redes de Computadores no SENAC São Paulo — Unidade Lapa Tito.
