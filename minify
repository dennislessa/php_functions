<?php

/**
 * Função que minifica uma string - remove espaços, linhas, tabulações.
 * 
 * @param String $buffer String que será minificada.
 * @return String
 */
function minify( $buffer ) {
    $buffer = preg_replace('/\/\*(.*)\*\//', '', $buffer);
    $buffer = str_replace(array("\n", "\r", "\n\r", "\t", "\r\n"), '', $buffer);
    $buffer = str_replace(array(': ', ' :'), ':', $buffer);
    $buffer = str_replace(array('; ', ' ;'), ';', $buffer);
    $buffer = str_replace(array('} ', ' }', ';}'), '}', $buffer);
    $buffer = str_replace(array('{ ', ' {'), '{', $buffer);
    $buffer = preg_replace('/ {2,}/', '', $buffer);

    return $buffer;
}

/**
 * Função que combina o conteúdo do conjunto de arquivos em um único arquivo.
 * 
 * @param Array $files      Array contendo os caminhos absolutos dos arquivos que 
 *                          serão combinados.
 * @param String $destin    String com o nome do arquivo destino que receberá a 
 *                          string resultante combinada e minificada.
 */
function join_files( array $files, $destin ) {
    if ( count($files) > 0 && file_exists($destin) ) {
        $buffer = '';

        foreach($files as $f) {
            $buffer .= file_get_contents( $f );
        }

        $buffer = minify( $buffer );

        file_put_contents( $destin, $buffer );
    }
}
