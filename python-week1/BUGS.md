# BUGS.md — Python Week 1

## BUG-001
- **Errore:** name 'items' is not defined
- **Nodo:** Code Python
- **Causa:** n8n Cloud 2.9.3 usa _items, non items
- **Soluzione:** sostituire items con _items in tutti i nodi Code Python
