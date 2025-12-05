## Explicacao
O objetivo e somente demonstrar uma relacao dO SOLID COM GOF4 NOS CRIACONAIS,
e detalhando e com uso de IA e eu conferindo agora realmente a base de codigo
pode ser semalhante, os princpios de forma escrita sao distintos ou meio
proximos..

Vou falar de partes voce usando tecnicas de poo que vc nao aprende na faculdade
somente quando programa mais do que o normal, composicao, injecao de dependencia,
associação e agregação que geralmente sao usadas nesses modelos voce pode ter seme
lhancas nos codigo. 

Factory methods e um SOLID DO SRP ATE O OPEN CLOSED PODEM SER PARECIDOS.

PERGUNTA PARA IA 
UM FACTORY METHO E IGUAL UM SOLID SRP E OPEN CLOSED?
bOA PROVOCAÇAÕ.
```
<?php

// Interface comum
interface Shape {
    public function area(): float;
}

// Implementações concretas
class Rectangle implements Shape {
    private float $width;
    private float $height;

    public function __construct(float $width, float $height) {
        $this->width = $width;
        $this->height = $height;
    }

    public function area(): float {
        return $this->width * $this->height;
    }
}

class Circle implements Shape {
    private float $radius;

    public function __construct(float $radius) {
        $this->radius = $radius;
    }

    public function area(): float {
        return pi() * $this->radius * $this->radius;
    }
}

class Square implements Shape {
    private float $side;

    public function __construct(float $side) {
        $this->side = $side;
    }

    public function area(): float {
        return $this->side * $this->side;
    }
}

// Factory Method
class ShapeFactory {
    public static function create(string $type, float $a, float $b = 0): ?Shape {
        return match ($type) {
            'rectangle' => new Rectangle($a, $b),
            'circle'    => new Circle($a),
            'square'    => new Square($a),
            default     => null,
        };
    }
}
```


// Uso
$rect = ShapeFactory::create('rectangle', 5, 10);
$circle = ShapeFactory::create('circle', 3);
$square = ShapeFactory::create('square', 4);

echo "Área do retângulo: " . $rect->area() . PHP_EOL;   // 50
echo "Área do círculo: " . $circle->area() . PHP_EOL;   // ~28.27
echo "Área do quadrado: " . $square->area() . PHP_EOL;  // 16

#RESPOSTA DA IA
##Como isso aplica SRP e OCP
• 	SRP (Single Responsibility Principle)
• 	Cada classe (, , ) tem uma única responsabilidade: calcular área da sua forma.
• 	A classe  tem uma única responsabilidade: criar objetos.
• 	Nenhuma classe mistura responsabilidades.
• 	OCP (Open/Closed Principle)
• 	O sistema está aberto para extensão: basta criar uma nova classe que implemente  (ex.: ).
• 	Está fechado para modificação: funções que usam  não precisam ser alteradas.
• 	O Factory pode ser estendido para suportar novos tipos sem quebrar código existente.

## Ganhos práticos em PHP
• 	Organização: separa criação de objetos da lógica de negócio.
• 	Extensibilidade: novos tipos de  podem ser adicionados sem alterar código cliente.
• 	Testabilidade: cada classe pode ser testada isoladamente.
• 	Manutenção: responsabilidades bem definidas reduzem acoplamento e bugs lógicos.
