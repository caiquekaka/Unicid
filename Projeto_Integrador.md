# Unicid
Projeto Integrador - UNICID

<!DOCTYPE html>
<html><head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Page Title</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" media="screen" href="main.css">
    <script src="main.js"></script>
    <script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>

    <style>
        body {
            margin: 0;
            width: 100vw;
            height: 100vh;
            display: flex;
            align-items: start;
            justify-content: center;
            font-family: sans-serif;
            padding-top: 50px;
            color: #383838;
        }

        .form-cadastro {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .container {
            padding: 10px;
            background: #FFF;
            border-radius: 6px;
            box-shadow: -2px 3px 6px #CCC;
            width: 100%;
            max-width: 400px;
        }

        .form {
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .lista-item.checked {
            text-decoration: line-through;
        }

        input,
        button {
            outline: none;
        }

        input[name="item"] {
            height: 30px;
            border: solid 1px #CCC;
            padding: 5px 12px;
            font-size: 15px;
            outline: none;
            color: #383838;
        }

        button {
            background: #7c7cbf;
            color: #FFF;
            border: none;
            height: 40px;
            margin-top: -6px;
            text-transform: uppercase;
            cursor: pointer;
        }

        .lista {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .lista-item {
            display: flex;
            align-items: center;
            gap: 7px;
            font-size: 16px;
        }

        h1 {
            font-size: 16px;
            font-weight: 100;
            text-transform: uppercase;
            color: #383838;
            margin: 0;
            margin-bottom: -8px;
        }

        p {
            font-size: 12px;
            margin: 0;
            color: #383838;
        }

        .trash {
            background-image: url("data:image/svg+xml,%3Csvg width='50px' height='50px' viewBox='0 0 50 50' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M20 18h2v16h-2z'/%3E%3Cpath d='M24 18h2v16h-2z'/%3E%3Cpath d='M28 18h2v16h-2z'/%3E%3Cpath d='M12 12h26v2H12z'/%3E%3Cpath d='M30 12h-2v-1c0-.6-.4-1-1-1h-4c-.6 0-1 .4-1 1v1h-2v-1c0-1.7 1.3-3 3-3h4c1.7 0 3 1.3 3 3v1z'/%3E%3Cpath d='M31 40H19c-1.6 0-3-1.3-3.2-2.9l-1.8-24 2-.2 1.8 24c0 .6.6 1.1 1.2 1.1h12c.6 0 1.1-.5 1.2-1.1l1.8-24 2 .2-1.8 24C34 38.7 32.6 40 31 40z'/%3E%3C/svg%3E");
            width: 23px;
            height: 23px;
            background-size: 100%;
            border: solid 1px;
            border-radius: 6px;
            cursor: pointer;
        }

        .text-item{
            flex: 1;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="form-cadastro">
            <h1>Lista de compras</h1>
            <p>Preencha a lista de compras abaixo e não esqueça nenhum item ao ir no supermercado</p>
            <div class="form">
                <input type="text" name="item">
                <button>Adicionar</button>
            </div>

            <div class="lista">
            </div>
        </div>
    </div>

    <script>
        const initButton = () => {
            $('input[name=item]').on('keypress', (e) => {
                if (e.keyCode == 13) {
                    const valItem = $('input[name=item]').val();
                    addItemList(valItem);
                }
            })

            $('button').on('click', () => {
                const valItem = $('input[name=item]').val();
                addItemList(valItem);
            })
        }

        const addItemList = (valItem) => {
            if (!valItem) return;

            const item = $(`
                <div class="lista-item">
                    <input type="checkbox" name="confirm" />
                    <div class="text-item">${$('input[name=item]').val()}</div>
                    <div class="trash"></div>
                </div>`);

            addEvent(item.find('input'))

            $('.lista').append(item);

            $('input[name=item]').val('');
        }

        const addEvent = (el) => {
            
            el.parent().find('.trash').on('click', (e) => {
                el.parent().remove()
            })

            el.on('click', (e) => {
                const el = $(e)[0].target;

                if (el.checked)
                    $(el).parent().addClass('checked')
                else
                    $(el).parent().removeClass('checked')
            })
        }

        initButton();
    </script>


</body></html>


