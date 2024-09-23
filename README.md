# Staking Contract

## Descripción del Contrato

Este contrato de staking de Ethereum permite a los usuarios bloquear tokens ERC-20 para ganar recompensas en función del tiempo que los tokens permanecen en staking. Los usuarios pueden participar en staking, retirar sus fondos y reclamar recompensas mediante interacciones definidas en el contrato. Las recompensas se calculan mediante un modelo de interés compuesto, basado en el tiempo desde la última interacción, lo que promueve una distribución equitativa y proporcionada del interés generado.

### Funcionalidades Principales

- **Stake Tokens**: Los usuarios pueden depositar tokens ERC-20 en el contrato.
- **Withdraw Tokens**: Permite a los usuarios retirar sus tokens en cualquier momento, sin perder las recompensas acumuladas hasta ese punto.
- **Claim Rewards**: Los usuarios pueden reclamar sus recompensas acumuladas, que se calculan con base en la cantidad de tiempo que sus tokens han estado en staking.

## Razonamiento detrás del Diseño

### Patrones de Diseño en Solidity

**1. Ownable:** Este patrón restringe las funciones críticas del contrato, como la pausa y la actualización del contrato, exclusivamente al propietario. Esto asegura una gestión centralizada en situaciones que requieren un control rápido y directo para la resolución de problemas o mejoras.

**2. Pausable:** Se implementa para habilitar la pausa del contrato en situaciones de emergencia o durante el mantenimiento, lo que ayuda a proteger los fondos de los usuarios y mantener la integridad del contrato.

**3. ReentrancyGuard:** Utilizado para proteger las funciones financieras del contrato contra ataques de reentrancia, aumentando la seguridad de los fondos de los usuarios.

**4. UUPS (Universal Upgradeable Proxy Standard):** Facilita la actualización del contrato sin la necesidad de migrar los tokens y los datos a un nuevo contrato, proporcionando una manera eficiente y segura de implementar mejoras y correcciones.

### Consideraciones Adicionales

**Interés Compuesto:** Implementamos un modelo de interés compuesto para calcular las recompensas, incentivando a los usuarios a mantener sus tokens en staking por períodos prolongados, lo que contribuye a la estabilidad y crecimiento del proyecto.

**Seguridad del Tesoro:** Antes de que los usuarios puedan reclamar sus recompensas, el contrato verifica que existan suficientes fondos en el tesoro para cubrir todas las recompensas pendientes, asegurando la sostenibilidad financiera del contrato.

## Integrantes del Equipo

- [Angelo Ramírez](https://github.com/angeloortega)
- [Ricardo Bonilla Morales](https://github.com/richbm10)

## Contrato en la Red Sepolia

- **Contrato Principal:** [Ver en Sepolia Etherscan](https://sepolia.etherscan.io/address/0xb49695ad627ea9b7be904a8459e79b49213c74a1)
- **Proxy Contract:** [Ver en Sepolia Etherscan](https://sepolia.etherscan.io/address/0x8996ed03dbb3d4251f04078e6632da85a259eaa1)

