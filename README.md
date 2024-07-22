# projeto_01
Lista de Tarefas 
# Declarar lista de tarefas
tasks = [{"description": "Tarefa 1", "completed": False}]

# Funções para listar as tarefas
def list_tasks():
    if tasks:
        print("Segue lista de tarefas:")
        for i, task in enumerate(tasks, start=1):
            status = "Concluída" if task["completed"] else "Pendente"
            print(f"{i}. {task['description']} - {status}")
    else:
        print("A lista de tarefas está vazia!")

# Funções para adicionar tarefa
def add_task():
    global tasks
    new_task = input("Descreva aqui a nova tarefa que deseja adicionar na lista de tarefas: ")
    tasks.append({"description": new_task, "completed": False})
    print("Tarefa adicionada com sucesso! Lista de tarefas atualizada:")
    list_tasks()

# Funções para remover tarefa
def remove_task():
    global tasks
    list_tasks()
    try:
        task_num = int(input("Indique o número do item que deseja remover da lista de tarefas: "))
        if 1 <= task_num <= len(tasks):
            removed_task = tasks.pop(task_num - 1)
            print(f"A tarefa '{removed_task['description']}' foi retirada da lista!")
        else:
            print("O número digitado é inválido!")
    except ValueError:
        print("Por favor, insira um número válido.")
    list_tasks()

# Funções para marcar tarefa como concluída
def complete_task():
    global tasks
    list_tasks()
    try:
        task_num = int(input("Digite o número da tarefa que deseja marcar como concluída: "))
        if 1 <= task_num <= len(tasks):
            tasks[task_num - 1]["completed"] = True
            print(f"Tarefa '{tasks[task_num - 1]['description']}' marcada como concluída!")
        else:
            print("Número de tarefa inválido.")
    except ValueError:
        print("Por favor, insira um número válido.")
    list_tasks()

# Função principal com loop e menu de opções
def main():
    while True:
        print("\nMenu de Opções:")
        print("1. Adicionar Tarefa")
        print("2. Listar Tarefas")
        print("3. Remover Tarefa")
        print("4. Marcar Tarefa como Concluída")
        print("5. Sair")

        try:
            choice = int(input("Escolha uma opção: "))
            if choice == 1:
                add_task()
            elif choice == 2:
                list_tasks()
            elif choice == 3:
                remove_task()
            elif choice == 4:
                complete_task()
            elif choice == 5:
                print("Saindo...")
                break
            else:
                print("Opção inválida. Por favor, escolha uma opção válida.")
        except ValueError:
            print("Entrada inválida. Por favor, insira um número.")

if __name__ == "__main__":
    main()
