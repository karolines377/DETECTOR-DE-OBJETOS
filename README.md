# Scanner com YOLO 🚀

Uma demonstração leve e interativa de detecção de objetos em tempo real utilizando **Streamlit** e **YOLOv8** (Ultralytics). Este projeto foi projetado como um protótipo rápido em arquivo único (`app.py`), ideal para fins educacionais e pronto para implantação imediata em plataformas de nuvem como o Render.

## 📌 Funcionalidades
* **Interface Web Intuitiva:** Construída inteiramente em Python com Streamlit.
* **Detecção de Objetos com IA:** Integração nativa com o modelo computacional YOLOv8 (versão Nano, otimizada para performance).
* **Captura em Tempo Real:** Utiliza o componente de câmera do dispositivo do usuário para capturar e processar imagens sob demanda.
* **Arquitetura Otimizada:** Implementação de cache (`@st.cache_resource`) para garantir que o modelo de IA seja carregado apenas uma vez na memória, economizando recursos do servidor.

---

## 🛠️ Tecnologias Utilizadas
* [Python 3.9+](https://www.python.org/)
* [Streamlit](https://streamlit.io/) (Interface gráfica e captura de mídia)
* [Ultralytics YOLOv8](https://docs.ultralytics.com/) (Processamento de visão computacional)
* [Pillow & NumPy](https://pillow.readthedocs.io/) (Manipulação de matrizes de imagem)

---

## 🚀 Como Executar Localmente

Siga os passos abaixo para clonar e rodar o projeto na sua máquina:

### 1. Clonar o repositório
```bash
git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
cd seu-repositorio
