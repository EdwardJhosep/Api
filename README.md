public function reniec($dni)
    {
        $token = 'apis-token-9121.qz-SBRzAN1zWNGrA1wYw6l2Dg7uatxrU';

        $client = new Client(['base_uri' => 'https://api.apis.net.pe', 'verify' => false]);

        try {
            $parameters = [
                'http_errors' => false,
                'connect_timeout' => 5,
                'headers' => [
                    'Authorization' => 'Bearer '.$token,
                    'Referer' => 'https://apis.net.pe/api-consulta-dni',
                    'User-Agent' => 'laravel/guzzle',
                    'Accept' => 'application/json',
                ],
                'query' => ['numero' => $dni],
            ];
            //Caonsulta a la APi
            $res = $client->request('GET', '/v2/reniec/dni', $parameters);
            $response = json_decode($res->getBody()->getContents(), true);

            return $response;
        } catch (\Exception $e) {
            return null;
        }
    }
