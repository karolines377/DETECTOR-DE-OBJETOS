import streamlit as st
from ultralytics import YOLO
from PIL import Image
import numpy as np

# Configuração inicial da página do Streamlit
st.set_page_config(
    page_title="Scanner com Yolo",
    layout="centered"
)

# Inicialização do modelo YOLO (utilizando cache para evitar recarregamento a cada interação)
@st.cache_resource
def cache_modelo_yolo():
    # Carrega a versão nano do YOLOv8, ideal para deploys leves e rápidos no Render
    return YOLO("yolov8n.pt")

model = cache_modelo_yolo()

# Título principal da aplicação
st.title("Scanner com YOLO")
st.write("Abra a câmera abaixo para realizar a detecção de objetos em tempo real por imagem.")

# Controle de estado para ativação da câmera através de botão
if "camera_ativa" not in st.session_state:
    st.session_state.camera_ativa = False

if st.button("Abrir Câmera"):
    st.session_state.camera_ativa = True

# Bloco lógico de captura e processamento da imagem
if st.session_state.camera_ativa:
    # Renderiza o componente nativo de câmera do Streamlit
    foto_capturada = st.camera_input("Posicione o objeto em frente à câmera")

    if foto_capturada:
        # Conversão do arquivo de imagem capturado para o formato legível pelo OpenCV/Pillow
        imagem_pil = Image.open(foto_capturada)
        imagem_np = np.array(imagem_pil)

        # Execução da inferência do modelo YOLO na imagem capturada
        resultados = model(imagem_np)

        # Renderização visual dos resultados (desenho de caixas delimitadoras e labels)
        imagem_anotada = resultados[0].plot()

        # Exibição do resultado final processado na interface do usuário
        st.subheader("Resultado da Detecção:")
        st.image(imagem_anotada, channels="RGB", use_container_width=True)
