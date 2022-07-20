# python-script-template
My interpretation of golden Python script template with logging configured to save a log with the same filename as the script.

```py
dir_path = os.path.dirname(os.path.realpath(__file__))
    log_filename = os.path.splitext(__file__)[0] + ".log"
    log_filepath = os.path.join(dir_path, log_filename)
    logging.basicConfig(
        level=logging.DEBUG,
        format="%(asctime)s [%(levelname)s] - %(message)s",
        datefmt="%d-%b-%y %H:%M:%S",
        handlers=[
            logging.FileHandler(log_filepath, mode="a"),
            logging.StreamHandler(),
        ],
    )
    logging.info("Started")
    try:
        # Main code goes here
        print("Hello World!")
    except Exception as e:
        logging.error(e, exc_info=True)
    finally:
        logging.info("Finished")
```
