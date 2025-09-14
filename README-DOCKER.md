# Vault Docker Setup

Este setup configura o HashiCorp Vault na sua rede `integrisoft-network`.

## Pré-requisitos

1. Docker e Docker Compose instalados
2. Rede `integrisoft-network` criada:
   ```bash
   docker network create integrisoft-network
   ```

## Como usar

### 1. Iniciar o Vault
```bash
docker-compose up -d
```

### 2. Verificar se está rodando
```bash
docker-compose ps
```

### 3. Acessar o Vault

- **Interface Web**: http://localhost:8200
- **Token de desenvolvimento**: `myroot`

### 4. Usar o CLI do Vault
```bash
# Entrar no container
docker-compose exec vault sh

# Ou usar o CLI diretamente
docker-compose exec vault vault status
```

### 5. Configurar variáveis de ambiente (opcional)
```bash
export VAULT_ADDR=http://localhost:8200
export VAULT_TOKEN=myroot
```

## Comandos úteis

```bash
# Ver logs
docker-compose logs -f vault

# Parar o serviço
docker-compose down

# Reiniciar
docker-compose restart vault

# Remover tudo (incluindo volumes)
docker-compose down -v
```

## Configuração

- **Configuração**: `vault-config/vault.hcl`
- **Dados**: Volume Docker `vault-data`
- **Logs**: Volume Docker `vault-logs`
- **Porta**: 8200
- **Rede**: integrisoft-network

## Modo Desenvolvimento

Este setup está configurado para desenvolvimento com:
- TLS desabilitado
- Token root pré-definido
- UI habilitada
- Storage em arquivo local

⚠️ **Não use em produção!**
