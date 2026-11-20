# Análise Comparativa de Modelos de Deep Learning para Detecção de Defeitos em Superfícies de Alumínio na Indústria 5.0

Este repositório reúne os notebooks experimentais e material de apoio do Trabalho de Conclusão de Curso de mesmo nome.

O objetivo é preparar uma versão do conjunto APDDD para detecção de objetos, treinar e avaliar variantes das famílias YOLO e RT-DETR e comparar sua qualidade de detecção e velocidade. No estudo, o RT-DETR Large obteve mAP@0.5 de 0,591 a 69 FPS. Esses valores são resultados reportados no trabalho; executar os notebooks novamente pode produzir resultados diferentes conforme hardware utilizado.

## Conteúdo do repositório

| Arquivo | Finalidade |
| --- | --- |
| **create_dataset.ipynb** | Reúne imagens, rótulos e amostras sem defeito; divide os dados e gera o YAML de configuração. |
| **YOLO11.ipynb** | Treina variantes Nano, Small, Medium, Large e Extra Large da YOLOv11. |
| **YOLO12.ipynb** | Treina as cinco variantes da YOLOv12. |
| **YOLO26.ipynb** | Treina as cinco variantes da YOLO26. |
| **RT-DETR.ipynb** | Treina as variantes Large e Extra Large do RT-DETR. |
| **validations.ipynb** | Carrega os pesos treinados e executa validações e comparações. |

## Requisitos

- Python e Jupyter Notebook ou JupyterLab, ou um ambiente compatível com notebooks, como Google Colab.
- PyTorch e Ultralytics. As versões usadas no servidor estão registradas em requirements.txt; torch e torchvision foram instalados para CUDA 11.8. Confira a compatibilidade com o ambiente de destino antes de instalar.
- Bibliotecas utilizadas pelos notebooks: scikit-learn, OpenCV, Matplotlib, Pillow, pandas e NumPy.
- O dataset, os melhores pesos e os registros dos treinamentos podem ser baixados pelo link na seção Downloads.
- GPU NVIDIA recomendada para reproduzir os treinamentos em tempo razoável. A disponibilidade e configuração de GPU dependem do ambiente.

O arquivo requirements.txt relata as versões utilizadas. torch e torchvision estão configurados para CUDA 11.8, confira a compatibilidade com o ambiente de destino antes de instalar. Para preparar o ambiente, use:

~~~bash
python -m pip install -r requirements.txt
~~~

Em ambientes sem GPU, pode ser necessário ajustar ou remover a configuração de dispositivos CUDA presente nos notebooks.

## Downloads

O dataset utilizado nos experimentos, os melhores pesos e os registros das execuções estão disponíveis nesta pasta do Google Drive:

[Baixar dataset, melhores pesos e registros dos treinamentos](https://drive.google.com/drive/u/0/folders/16O2msu5wes2TfsdnSNTJtCn7uho3aTpk)

Os arquivos não são versionados neste repositório por seu tamanho. Após o download, descompacte os arquivos na raiz do projeto para manter o caminho pré-configurado nos notebooks.

## Dados e diretórios esperados

~~~text
workspace/
└── TCC2/
    ├── create_dataset.ipynb
    ├── YOLO11.ipynb
    ├── YOLO12.ipynb
    ├── YOLO26.ipynb
    ├── RT-DETR.ipynb
    ├── validations.ipynb
    ├── runs/detect/                     # pesos e registros baixados ou gerados
    └── dataset_APDDD_completo/            # dataset baixado
~~~

O notebook create_dataset.ipynb foi incluído no repositório para registro de como a divisão dos dados foi feita, entretanto não é possível executá-lo novamente sem as pastas originais APSPC1 e APSPC2, os quais podem ser baixados pelas referências oficiais citadas no trabalho.

## Como executar

1. Baixe o dataset, os pesos e os registros pela seção Downloads e extraia-os preservando os caminhos relativos descritos acima
2. Preserve o caminho já configurado nos notebooks
3. Abra e execute os notebooks de treinamento dos modelos que deseja avaliar: **YOLO11.ipynb**, **YOLO12.ipynb**, **YOLO26.ipynb** e/ou **RT-DETR.ipynb**. Cada notebook baixa/carrega os pesos iniciais do modelo por meio do Ultralytics e salva os resultados em runs/detect/, sob os nomes configurados nas chamadas de treinamento.
4. Abra **validations.ipynb** para validar e comparar os pesos. O notebook espera os arquivos `best.pt` nas pastas `runs/detect/.../weights/` configuradas em suas células. Use os pesos baixados ou treine os modelos correspondentes antes da validação.
5. Registre versões das bibliotecas, hardware, alterações nos parâmetros e sementes ao reproduzir ou comparar resultados.


## Observações sobre os notebooks

- Os notebooks contêm comandos de configuração de CUDA específicos de shell. Caso o ambiente seja diferente daquele em que o notebook foi preparado, ajuste esses comandos para o sistema utilizado.
- Confira o nome de saída dos treinamentos antes de executar novamente. Os notebooks gravam em runs/detect/, e algumas células de continuação/validação pressupõem nomes e pesos específicos.
- Dados, pesos e registros não são versionados no repositório Git; podem ser baixados pelo link da seção Downloads ou regenerados executando os notebooks.

## Citação

Se utilizar este código em pesquisa ou em trabalho acadêmico, cite o Trabalho de Conclusão de Curso correspondente e indique a versão do repositório utilizada. Consulte o texto acadêmico para os dados bibliográficos completos e as referências do conjunto APDDD.






