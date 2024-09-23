# Staking Contract

## Descripción del Contrato

Este contrato de staking permite a los usuarios bloquear tokens ERC-20 en el contrato para ganar recompensas basadas en la cantidad de tokens apostados y el tiempo que se mantienen en staking. Los usuarios pueden apostar, retirar y reclamar recompensas a través de interacciones con funciones específicas del contrato. Las recompensas se calculan usando un interés compuesto con un tiempo basado en la última interacción del usuario, asegurando una distribución justa de recompensas basadas en el tiempo.

## Razonamiento detrás del Diseño

### Patrones de Diseño en Solidity

**1. Ownable:** Este patrón se utiliza para restringir el acceso a funciones críticas como pausar o despausar el contrato, y actualizar el contrato, asegurando que solo el propietario del contrato pueda realizar estas acciones.

**2. Pausable:** Implementado para permitir que el contrato se pause en caso de emergencias o mantenimiento, deteniendo las operaciones críticas como apostar y retirar para proteger a los usuarios y sus fondos.

**3. ReentrancyGuard:** Se utiliza para prevenir ataques de reentrancia en funciones como `stake`, `withdraw`, y `claimReward`, que podrían ser explotadas para drenar fondos del contrato.

**4. UUPS (Universal Upgradeable Proxy Standard):** Se eligió este patrón para permitir actualizaciones del contrato sin la necesidad de migrar los tokens y los datos a un nuevo contrato, lo que proporciona una flexibilidad significativa y reduce el riesgo de errores durante las migraciones.

### Consideraciones Adicionales

**Interés Compuesto:** Se implementó el cálculo de interés compuesto para las recompensas para incentivar a los usuarios a mantener sus tokens en staking por períodos más largos, aumentando así la estabilidad del token y el proyecto.

**Seguridad del Tesoro:** Antes de permitir que los usuarios reclamen recompensas, el contrato verifica que el tesoro tenga suficientes fondos para cubrir la recompensa, protegiendo el contrato contra la depleción de fondos.

## Integrantes del Equipo

- [Angelo Ramírez](https://github.com/angeloortega)
- [Ricardo Bonilla Morales](https://github.com/richbm10)}

## Contrato en la red SepoliaEth
- https://sepolia.etherscan.io/address/0xb49695ad627ea9b7be904a8459e79b49213c74a1
- proxy (https://sepolia.etherscan.io/address/0x8996ed03dbb3d4251f04078e6632da85a259eaa1)



