// интерфейс логгера interface Logger { log(message: string): void; }

// создается класс потера class Plotter { private logger: Logger; private x: number; private y: number; private color: string; private isCarriageDown: boolean;

constructor(logger: Logger) { this.logger = logger; this.x = 0; this.y = 0; this.color = 'black'; this.isCarriageDown = false; }

setcolor(color: string): void { this.color = color; this.logger.log(Устанавливаем ${color} цвет линии.); }

carriagedown(): void { this.isCarriageDown = true; this.logger.log('Опускаем каретку.'); }

move(distance: number): void { const newX = this.x + distance; const newY = this.y; this.logger.log(Чертим линию из (${this.x}, ${this.y}) в (${newX}, ${newY}) используя ${this.color} цвет.); this.x = newX; this.y = newY; }

carriageup(): void { this.isCarriageDown = false; this.logger.log('Поднимаем каретку.'); }

turn(angle: number): void { this.logger.log(Поворачиваем на ${angle} градусов.); } }

class LogToConsole implements Logger { log(message: string): void { console.log(message); } }

function drawtriangle(plt: Plotter, size: number): void{ plt.setcolor('green'); for (let i=0; i<3; ++i){ plt.carriagedown(); plt.move(size); plt.carriageup(); plt.turn(120.0); } }

const plotter = new Plotter(new LogToConsole()); drawtriangle(plotter, 100.0);
