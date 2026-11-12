#include <iostream>
#include <queue>
#include <string>

struct Ticket {
    int id;
    std::string cliente;
    std::string incidencia;
};

int main() {
    std::queue<Ticket> colaSoporte;

    std::cout << "=== RECEPCION DE TICKETS ===\n";
    colaSoporte.push({101, "Ana Gomez", "Error de autenticacion en portal"});
    colaSoporte.push({102, "Carlos Ruiz", "Solicitud de cambio de clave"});
    colaSoporte.push({103, "Elena Torres", "Discrepancia en facturacion"});

    std::cout << "Tickets en espera: " << colaSoporte.size() << "\n\n";
    std::cout << "Proximo en ser atendido (front): #" << colaSoporte.front().id 
              << " - " << colaSoporte.front().cliente << "\n";
    std::cout << "Ultimo en ingresar (back):       #" << colaSoporte.back().id 
              << " - " << colaSoporte.back().cliente << "\n\n";

    std::cout << "=== PROCESAMIENTO DE ATENCION (FIFO) ===\n";
    while (!colaSoporte.empty()) {
        const Ticket& actual = colaSoporte.front();

        std::cout << "Atendiendo Ticket #" << actual.id 
                  << " | Cliente: " << actual.cliente 
                  << " | Motivo: " << actual.incidencia << "\n";
        colaSoporte.pop();
    }

    if (colaSoporte.empty()) {
        std::cout << "\n[OK] Todos los tickets han sido procesados en orden de llegada.\n";
    }

    return 0;
}
