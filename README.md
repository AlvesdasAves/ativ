# ativ
menu() {
  echo "Escolha uma operação matemática:"
  echo "1. Adição"
  echo "2. Subtração"
  echo "3. Multiplicação"
  echo "4. Divisão"
  read -p "Digite a sua escolha (1/2/3/4): " choice
}


calculate() {
  case $choice in
    1)
      result=$(echo "$num1 + $num2" | bc)
      echo "Resultado da Adição: $result"
      ;;
    2)
      result=$(echo "$num1 - $num2" | bc)
      echo "Resultado da Subtração: $result"
      ;;
    3)
      result=$(echo "$num1 * $num2" | bc)
      echo "Resultado da Multiplicação: $result"
      ;;
    4)
      if [ "$num2" -ne 0 ]; then
        result=$(echo "scale=2; $num1 / $num2" | bc)
        echo "Resultado da Divisão: $result"
      else
        echo "Erro: Divisão por zero não é permitida."
      fi
      ;;
    *)
      echo "Escolha inválida."
      ;;
  esac
}


read -p "Digite o primeiro número: " num1
read -p "Digite o segundo número: " num2


menu


calculate

chmod +x calculadora.sh


./calculadora.sh

