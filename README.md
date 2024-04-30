Atividade de Principios de SOLID

1- responsabilidade única 
          
    #include <iostream>
    #include <string>
    
    // Classe para manipulação de arquivos
    class FileManager {
    public:
        void readFile(const std::string& filename) {
            std::cout << "Lendo o arquivo: " << filename << std::endl;
            // Lógica para ler o arquivo
        }
    
        void writeFile(const std::string& filename, const std::string& content) {
            std::cout << "Escrevendo no arquivo: " << filename << std::endl;
            // Lógica para escrever no arquivo
        }
    };
    
    // Classe para manipulação de dados
    class DataProcessor {
    public:
        void processData(const std::string& data) {
            std::cout << "Processando os dados: " << data << std::endl;
            // Lógica para processar os dados
        }
    };
    
    int main() {
        FileManager fileManager;
        DataProcessor dataProcessor;
    
        // Lendo o arquivo
        fileManager.readFile("dados.txt");
    
        // Processando os dados lidos do arquivo
        std::string data = "Dados lidos do arquivo";
        dataProcessor.processData(data);
    
        // Escrevendo no arquivo
        fileManager.writeFile("resultado.txt", data);
    
        return 0;
    }
Neste exemplo, a classe FileManager lida apenas com a parte de mexer nos arquivos (leitura e escrita), 
enquanto a classe DataProcessor cuida somente de processar os dados. Cada classe tem sua função específica
e pode ser modificada sem afetar a outra.

2- Aberto/Fechado

    interface Remuneravel
    {
        public function remuneracao();
    }
    
    class ContratoClt implements Remuneravel
    {
        public function remuneracao()
        {
            //...
        }
    }
    
    class Estagio implements Remuneravel
    {
        public function remuneracao()
        {
            //...
        }
    }
    
    class FolhaDePagamento
    {
        protected $saldo;
        
        public function calcular(Remuneravel $funcionario)
        {
            $this->saldo = $funcionario->remuneracao();
        }
    }

Esse código segue o Princípio Aberto/Fechado porque permite adicionar novos tipos de funcionários remuneráveis sem ter que mexer
no código que já existe. Isso é possível porque as classes ContratoClt e Estagio implementam a interface Remuneravel, então a
FolhaDePagamento consegue calcular a remuneração de qualquer tipo de funcionário que siga esse padrão, assim podemos estender o
sistema sem precisar mexer no código.
    
3- Liskov Substitution Principle (LSP)
    
    #include <iostream>
    
    // Classe base que representa um animal
    class Animal {
    public:
        virtual void makeSound() const {
            std::cout << "Animal fazendo um som." << std::endl;
        }
    };
    
    // Classe derivada que representa um cachorro
    class Dog : public Animal {
    public:
        void makeSound() const override {
            std::cout << "Latindo: Au Au!" << std::endl;
        }
    };
    
    // Função que faz um animal fazer um som
    void letAnimalMakeSound(const Animal& animal) {
        animal.makeSound();
    }
    
    int main() {
        Animal genericAnimal;
        Dog myDog;
    
        letAnimalMakeSound(genericAnimal); // Um animal genérico faz um som
        letAnimalMakeSound(myDog);         // Um cachorro faz um som específico (latido)
    
        return 0;
    }

Nesse exemplo, a classe Animal tem um método makeSound() que mostra qual som um animal faz. A classe Dog, que é uma subclasse,
muda esse método para representar o som de um cachorro (latido). A função letAnimalMakeSound() pode aceitarum som de qualquer animal como 
argumento, seja um animal qualquer ou um cachorro, respeitando o Princípio de Substituição de Liskov.


