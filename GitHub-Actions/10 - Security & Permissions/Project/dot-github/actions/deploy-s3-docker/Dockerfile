#####################################
#                                   #
#  @author      : 00xWolf           #
#    GitHub    : @mmsaeed509       #
#    Developer : Mahmoud Mohamed   #
#  﫥  Copyright : Exodia OS         #
#                                   #
#####################################

FROM python:3

COPY requirements.txt /requirements.txt

RUN pip install -r requirements.txt

COPY deployment.py /deployment.py

CMD ["python", "/deployment.py"]