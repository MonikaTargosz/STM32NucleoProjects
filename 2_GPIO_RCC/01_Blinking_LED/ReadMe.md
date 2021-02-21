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


# Technical data - configuration

### Commercial Port Number: 
NUCLEO-F411RE

### Targeted Language: 
C

### Taggeted Binany Type: 
Executable

### Targgeted Project Type: 
STM32 Cube
