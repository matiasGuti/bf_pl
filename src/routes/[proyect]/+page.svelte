<script lang="ts">
	import { Avatar, AvatarImage, AvatarFallback } from "$lib/components/ui/avatar";
	import { Badge } from "$lib/components/ui/badge";
	import { Card, CardContent, CardHeader, CardTitle } from "$lib/components/ui/card";
	import { Button } from "$lib/components/ui/button";
	import { FileText, FileSpreadsheet } from "lucide-svelte";;

	const proyecto = {
		nombre: "Diagnóstico de Infraestructura en Azure",
		periodo: "Enero 2023 - Junio 2023",
		tags: ["Azure", "Diagnóstico", "Databricks"],
		detalle: "Este proyecto se enfocó en realizar un diagnóstico completo de la infraestructura existente en Azure, utilizando herramientas avanzadas como Databricks para el análisis de datos y la optimización de recursos.",
		participantes: [
			{ nombre: "Ana García", cargo: "Líder de Proyecto", foto: "/images/user.png" },
			{ nombre: "Carlos Pérez", cargo: "Arquitecto de Soluciones", foto: "/images/user.png" },
			{ nombre: "Laura Martínez", cargo: "Analista de Datos", foto: "/images/user.png" },
		],
		archivos: [
			{ nombre: "Presentación Final.ppt", tipo: "ppt" },
			{ nombre: "Análisis de Costos.xlsx", tipo: "excel" },
		],
	};
</script>

<div class="min-h-screen bg-black text-white p-8">
	<div class="max-w-4xl mx-auto">
		<div class="flex justify-between items-start mb-8">
			<div>
				<h1 class="text-3xl font-bold mb-2">{proyecto.nombre}</h1>
				<p class="text-gray-400 mb-4">{proyecto.periodo}</p>
				<div class="flex flex-wrap gap-2">
					{#each proyecto.tags as tag}
						<Badge variant="outline" class="bg-[#19B9CB] text-white">{tag}</Badge>
					{/each}
				</div>
			</div>
			<img src="/images/logo.png" alt="Logo de la empresa" class="w-24 h-24 object-contain" />
		</div>

		<Card class="bg-gray-900 text-white mb-8">
			<CardContent class="pt-6">
				<p>{proyecto.detalle}</p>
			</CardContent>
		</Card>

		<h2 class="text-2xl font-semibold mb-4">Participantes</h2>
		<div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
			{#each proyecto.participantes as participante}
				<Card class="bg-gray-900 text-white">
					<CardHeader>
						<div class="flex items-center space-x-4">
							<Avatar>
								<AvatarImage src={participante.foto} alt={participante.nombre} />
								<AvatarFallback>{participante.nombre.charAt(0)}</AvatarFallback>
							</Avatar>
							<div>
								<CardTitle class="text-lg">{participante.nombre}</CardTitle>
								<p class="text-sm text-gray-400">{participante.cargo}</p>
							</div>
						</div>
					</CardHeader>
				</Card>
			{/each}
		</div>

		<h2 class="text-2xl font-semibold mb-4">Archivos Importantes</h2>
		<div class="grid grid-cols-1 md:grid-cols-2 gap-4">
			{#each proyecto.archivos as archivo}
				<Button variant="outline" class="bg-gray-900 text-white hover:bg-[#19B9CB] hover:text-black justify-start">
					{#if archivo.tipo === "ppt"}
						<FileText class="mr-2 h-4 w-4" />
					{:else if archivo.tipo === "excel"}
						<FileSpreadsheet class="mr-2 h-4 w-4" />
					{/if}
					{archivo.nombre}
				</Button>
			{/each}
		</div>
	</div>
</div>