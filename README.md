import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { motion } from "framer-motion";

// Versión avanzada del prototipo
// Concepto: plataforma que analiza ideas, genera modelos de negocio
// y propone automatizaciones con IA para emprendedores.

export default function AutoNegocioAI() {
  const [idea, setIdea] = useState("");
  const [analysis, setAnalysis] = useState(null);
  const [loading, setLoading] = useState(false);

  async function analyzeIdea() {
    if (!idea) return;

    setLoading(true);

    // Simulación de respuesta IA
    const simulatedResponse = {
      demand: "Alta",
      trend: "Economía de automatización y micro‑SaaS",
      problem:
        "Millones de pequeños negocios siguen gestionando clientes, pedidos e inventario manualmente.",
      opportunity:
        "Crear herramientas simples conectadas a WhatsApp para gestionar pedidos automáticamente.",
      monetization:
        "Modelo SaaS por suscripción mensual entre 5 y 20 USD.",
      controversialEdge:
        "Usar IA para crear micro‑negocios automatizados que operen casi sin intervención humana."
    };

    setTimeout(() => {
      setAnalysis(simulatedResponse);
      setLoading(false);
    }, 1200);
  }

  return (
    <div className="min-h-screen bg-gradient-to-b from-gray-50 to-gray-200 p-6 grid gap-6">
      <motion.h1
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        className="text-4xl font-bold"
      >
        AutoNegocio AI
      </motion.h1>

      <Card className="rounded-2xl shadow-xl">
        <CardContent className="p-6 grid gap-4">
          <p className="text-lg">
            Plataforma experimental para analizar ideas de negocio y crear
            sistemas automáticos de emprendimiento usando inteligencia
            artificial.
          </p>

          <Textarea
            placeholder="Describe un problema o idea de negocio..."
            value={idea}
            onChange={(e) => setIdea(e.target.value)}
          />

          <Button onClick={analyzeIdea}>
            {loading ? "Analizando con IA..." : "Analizar idea"}
          </Button>
        </CardContent>
      </Card>

      {analysis && (
        <Card className="rounded-2xl shadow-xl">
          <CardContent className="p-6 grid gap-3">
            <h2 className="text-2xl font-semibold">Análisis estratégico</h2>

            <p>
              <strong>Demanda del mercado:</strong> {analysis.demand}
            </p>

            <p>
              <strong>Tendencia tecnológica:</strong> {analysis.trend}
            </p>

            <p>
              <strong>Problema detectado:</strong> {analysis.problem}
            </p>

            <p>
              <strong>Oportunidad:</strong> {analysis.opportunity}
            </p>

            <p>
              <strong>Modelo de ingresos:</strong> {analysis.monetization}
            </p>

            <p>
              <strong>Elemento disruptivo:</strong> {analysis.controversialEdge}
            </p>
          </CardContent>
        </Card>
      )}
    </div>
  );
}
