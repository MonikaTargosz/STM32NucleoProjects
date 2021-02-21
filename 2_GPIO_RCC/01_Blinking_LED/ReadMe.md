# Description

The code is in int main.c in the while (1) loop because we want to blink the LED continuously.

# The code snippet

```
  while (1)
  {
    /* USER CODE END WHILE */
	  HAL_GPIO_WritePin(LD2_GPIO_Port, LD2_Pin, GPIO_PIN_SET);
	  HAL_Delay(500);
	  HAL_GPIO_WritePin(LD2_GPIO_Port, LD2_Pin, GPIO_PIN_RESET);
	  HAL_Delay(500);
    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
```

Using HAL_GPIO_TogglePin () to change pin state. It does not take the value of what it is supposed to be, it just changes the current one to the opposite.

```
  while (1)
  {
    /* USER CODE END WHILE */
	  HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
	  HAL_Delay(300);
    /* USER CODE BEGIN 3 */
  }
  /* USER CODE END 3 */
```

# Technical data - configuration

### Commercial Port Number: 
NUCLEO-F411RE

### Targeted Language: 
C

### Taggeted Binany Type: 
Executable

### Targgeted Project Type: 
STM32 Cube
