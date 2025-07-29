function conect {

    param($destino)

  

    if (-not $destino) {

        Write-Host "Uso: conect <nombre_maquina>"

        return

    }

  #  Write-Host "Prueba de alias $Destino "

    $usuarioGateway = $env:GATEWAY_USER

    $gateway = $env:GATEWAY_IP

    $usuarioDestino = $env:GATEWAY_USER

    $rsa = $env:RSA_KEY_PATH

    $sftp1= "AOTLXPRFTP00001"

    $sftp2= "AOTLXPRFTP00002"

  

    if ($destino -eq $sftp1 -or $destino -eq $sftp2 -or $destino -eq "prcs30pr") {

        ssh -i "C:\Users\Adrian Alonso\.ssh\id_rsa" -o "KexAlgorithms=+diffie-hellman-group14-sha1" -o "HostKeyAlgorithms=+ssh-rsa" -o "PubkeyAcceptedAlgorithms=+ssh-rsa" -o "MACs=+hmac-sha1" -J "$usuarioGateway@$gateway" "$usuarioDestino@$destino"

  

    }        

  

    ssh -i "$rsa" -J "$usuarioGateway@$gateway" "$usuarioDestino@$destino"

  

}

  

function adm01 {

  #  Write-Host "Prueba de alias $Destino "

    $usuarioGateway = $env:GATEWAY_USER

    $gateway = $env:GATEWAY_IP

    ssh "$usuarioGateway@$gateway"

}