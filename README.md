## PrettyPipeline 

### goals ⛳
- hydra를 이해한다
- config 관리를 fancy하게 한다
- 나만의 아름다운 파이프라인을 만든다

### steps 🌄
- [x] clone repo & environment setting
- [x] 그냥 실행. `python train.py`
- [x] config 하나를 바꿔서 실행 `python train.py +train.minist.input_size=512`

✖️ gpu를 지정할 수 있게 config를 바꿔본다(cuda, torch 호환 문제 때문에 안됨)

`hydra.utils.instantiate`로 객체도 만들 수가 있다
```
trainer: Trainer = hydra.utils.instantiate(
        config.trainer, callbacks=callbacks, logger=logger, _convert_="partial"
    )
```
config.trainer
```
defaults:
  - default.yaml

gpus: 4
strategy: ddp
sync_batchnorm: True
````


- [ ] mnist 모델말고 다운받은 데이터셋을 사용하여 학습을 돌려본다
- [ ] mnist 말고 간단한 모델을 만들어 본다


### materials 🗃️
- hydra 번역 doc : https://pjt3591oo.github.io/hydra_translate/build/html/index.html
- omegaconf + yaml은 variable 기능이 있음 : https://omegaconf.readthedocs.io/en/latest/usage.html#variable-interpolation
- path 설정은 이렇게 하면 될까? : `dotenv` or [omegaconf-env](https://omegaconf.readthedocs.io/en/latest/custom_resolvers.html#oc-env) ? 
