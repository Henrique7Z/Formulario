document.addEventListener("DOMContentLoaded", function () {
    const form = document.getElementById("pacienteForm");
    const nomeInput = document.getElementById("nome");
    const cpfInput = document.getElementById("cpf");
    const telefoneInput = document.getElementById("telefone");
    const emailInput = document.getElementById("email");
    const dataNascimentoInput = document.getElementById("datanascimento");

    let pacientes = [];

    form.addEventListener("submit", function (event) {
        event.preventDefault();

        const nome = nomeInput.value.trim();
        const cpf = cpfInput.value.trim();
        const telefone = telefoneInput.value.trim();
        const email = emailInput.value.trim();
        const dataNascimento = dataNascimentoInput.value.trim();

        if (!validarNome(nome)) {
            alert("O nome deve ter no máximo 100 caracteres.");
            return;
        }

        if (!validarCPF(cpf)) {
            alert("CPF inválido! Digite um CPF válido.");
            return;
        }

        if (pacientes.includes(cpf)) {
            alert("Este CPF já está cadastrado!");
            return;
        }

        if (!validarTelefone(telefone)) {
            alert("Telefone inválido! Use o formato: (XX) XXXXX-XXXX.");
            return;
        }

        if (!validarEmail(email)) {
            alert("E-mail inválido! Digite um e-mail válido.");
            return;
        }

        if (!validarDataNascimento(dataNascimento)) {
            alert("Data de nascimento inválida!");
            return;
        }

        pacientes.push(cpf);
        alert("Paciente cadastrado com sucesso!");

        form.reset();
    });

    function validarNome(nome) {
        return nome.length > 0 && nome.length <= 100;
    }

    function validarCPF(cpf) {
        cpf = cpf.replace(/\D/g, ""); 
        if (cpf.length !== 11 || /^(\d)\1{10}$/.test(cpf)) return false;

        let soma = 0, resto;
        for (let i = 0; i < 9; i++) soma += parseInt(cpf[i]) * (10 - i);
        resto = (soma * 10) % 11;
        if (resto === 10 || resto === 11) resto = 0;
        if (resto !== parseInt(cpf[9])) return false;

        soma = 0;
        for (let i = 0; i < 10; i++) soma += parseInt(cpf[i]) * (11 - i);
        resto = (soma * 10) % 11;
        if (resto === 10 || resto === 11) resto = 0;
        return resto === parseInt(cpf[10]);
    }

    function validarTelefone(telefone) {
        const telefoneRegex = /^\(\d{2}\) \d{4,5}-\d{4}$/;
        return telefoneRegex.test(telefone);
    }

    function validarEmail(email) {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailRegex.test(email);
    }

    function validarDataNascimento(data) {
        const hoje = new Date();
        const nascimento = new Date(data);
        return nascimento < hoje; 
    }
});
